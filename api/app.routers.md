# app.routers package

## Submodules

## app.routers.collection_delete module

FastAPI router for collection deleting.

### *async* app.routers.collection_delete.collection_delete(request: Request, collection_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_admin)) → [CollectionDeleteResponse](app.schemas.md#app.schemas.collection_delete.CollectionDeleteResponse)

Delete a collection and all its documents (including thumbnails,
revisions, and head files).

Disk cleanup is best-effort: missing thumbnails/revisions/head
files are ignored. A WRITE lock on the collection is taken to
block concurrent file operations during deletion.

**Authentication:**
- Requires a valid bearer token with admin role.

**Path parameters:**
- collection_id (integer ≥ 1): collection identifier.

**Response:**
- CollectionDeleteResponse — returns the deleted collection ID.

**Response codes:**
- 200 — collection deleted.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — collection not found.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Side effects:**
- Removes thumbnails, revisions, and head files from the filesystem
(best-effort); purges LRU cache entries.

**Hooks:**
- HOOK_AFTER_COLLECTION_DELETE — executed after successful
deletion.

## app.routers.collection_insert module

FastAPI router for creating collections.

### *async* app.routers.collection_insert.collection_insert(request: Request, schema: [CollectionInsertRequest](app.schemas.md#app.schemas.collection_insert.CollectionInsertRequest), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_write)) → [CollectionInsertResponse](app.schemas.md#app.schemas.collection_insert.CollectionInsertResponse)

Create a new collection and a matching directory on the filesystem,
then return the ID. The collection name must be unique; if a name
is already taken, the request is rejected.

**Authentication:**
- Requires a valid bearer token with writer role or higher.

**Validation schemas:**
- CollectionInsertRequest — request body with read-only flag,
name, and optional summary.
- CollectionInsertResponse — contains the newly created
collection ID.

**Request body:**
- readonly (boolean): read-only flag for the collection.
- name (string, 1-256; ≤255 UTF-8 bytes): collection name;
trimmed; / and NUL are not allowed.
- summary (string, 0-4096): optional description; trimmed; empty
becomes NULL.

**Response codes:**
- 201 — collection successfully created.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 422 — name already exists or fails validation.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Side effects:**
- Creates a directory at documents/<name>.

**Hooks:**
- HOOK_AFTER_COLLECTION_INSERT: executed after collection and
directory are successfully created.

## app.routers.collection_list module

FastAPI router for collection listing.

### *async* app.routers.collection_list.collection_list(request: Request, schema=Depends(CollectionListRequest), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [CollectionListResponse](app.schemas.md#app.schemas.collection_list.CollectionListResponse)

Retrieve collections matching the provided filters and return them
with the total number of matches.

**Authentication**
- Requires a valid bearer token with reader role or higher.

**Query parameters**
- CollectionListRequest — optional filters (creation time, creator,
readonly flag, name), pagination (offset/limit), and ordering
(order_by/order).

**Response**
- CollectionListResponse — page of collections and total match
count.

**Response codes**
- 200 — collection list returned.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks**
- HOOK_AFTER_COLLECTION_LIST — executed after successful retrieval.

## app.routers.collection_select module

FastAPI router for retrieving collection details by ID.

### *async* app.routers.collection_select.collection_select(request: Request, collection_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [CollectionSelectResponse](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse)

Retrieve a single collection by ID and return its details, including
creator info, creation and updateion timestamps, read-only flag,
name, and optional summary.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Response schema:**
- CollectionSelectResponse — includes collection ID; creator;
creation and last-update timestamps (Unix seconds, UTC); read-only
flag; normalized name; and optional summary.

**Path parameters:**
- collection_id (integer): identifier of the collection to
retrieve.

**Response codes:**
- 200 — collection found; details returned.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — collection not found.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_COLLECTION_SELECT: executed after a successful
retrieval.

## app.routers.collection_update module

### *async* app.routers.collection_update.collection_update(request: Request, schema: [CollectionUpdateRequest](app.schemas.md#app.schemas.collection_update.CollectionUpdateRequest), collection_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_edit)) → [CollectionUpdateResponse](app.schemas.md#app.schemas.collection_update.CollectionUpdateResponse)

Updates a collection’s properties and, if the name changes, renames
the underlying directory on disk. The operation updates: name,
readonly status, and summary. Changes are performed under an
exclusive collection lock to keep the database and filesystem in
sync. Collection names are unique across the application; both the
database and the filesystem are validated before applying changes.

**Authentication:**
- Requires a valid bearer token with editor role or higher.

**Validation schemas:**
- CollectionUpdateRequest — optional fields: name, readonly,

> summary.
- CollectionUpdateResponse — returns collection_id.

**Path parameters:**
- collection_id (integer ≥ 1) — collection identifier.

**Request body:**
- application/json with any of: name, readonly, summary.

**Response codes:**
- 200 — update successful.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or

> suspended.
- 404 — collection not found.
- 422 — validation error (e.g., name already exists).
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Locks & consistency:**
- Exclusive per-collection lock during the update.
- On rename, directory existence is checked before moving; any
failure triggers a best-effort rollback of the directory move.

**Hooks:**
- HOOK_AFTER_COLLECTION_UPDATE — executed after a successful
update.

## app.routers.document_delete module

FastAPI router for document deleting.

### *async* app.routers.document_delete.document_delete(request: Request, collection_id: int = Path(PydanticUndefined), document_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_admin)) → [DocumentDeleteResponse](app.schemas.md#app.schemas.document_delete.DocumentDeleteResponse)

Delete a document and all associated artifacts (thumbnail,
revisions, head file).

**Authentication:**
- Requires a valid bearer token with admin role.

**Path parameters:**
- collection_id (integer ≥ 1): parent collection identifier.
- document_id (integer ≥ 1): document identifier.

**Response:**
- DocumentDeleteResponse with document ID and latest revision
number.

**Response codes:**
- 200 — document deleted successfully.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — collection or document not found.
- 409 — conflict: thumbnail, revision or head file is missing.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Side effects:**
- Deletes thumbnail, all revisions, and the head file from the
filesystem; purges LRU cache entries.

**Hooks:**
- HOOK_AFTER_DOCUMENT_DELETE — executed after successful deletion.

## app.routers.document_download module

FastAPI router for file downloading.

### *async* app.routers.document_download.document_download(request: Request, collection_id: int = Path(PydanticUndefined), document_id: int = Path(PydanticUndefined), revision_number: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → Response

Download a document file (current head or a specific revision)
within a given collection. Returns the raw file bytes with the
document’s MIME type, and the original filename.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Path parameters:**
- collection_id (integer ≥ 1): parent collection identifier.
- document_id (integer ≥ 1): document identifier.
- revision_number (integer ≥ 0): 0 for the current file head;
> 0 for a specific revision.

**Response codes:**
- 200 — file returned.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — collection, document, or revision not found.
- 409 — file not found on filesystem or checksum mismatch.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_DOCUMENT_DOWNLOAD — executed after a successful read.

## app.routers.document_list module

FastAPI router for document listing.

### *async* app.routers.document_list.document_list(request: Request, schema=Depends(DocumentListRequest), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [DocumentListResponse](app.schemas.md#app.schemas.document_list.DocumentListResponse)

Retrieve documents matching the provided filters and return them
with the total number of matches.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Query parameters:**
- DocumentListRequest — optional filters (collection_id, creation
time, creator, flagged status, filename/mimetype, file size),
pagination (offset and limit), and ordering (order_by and order).

**Response:**
- DocumentListResponse — page of documents and total match count.

**Response codes:**
- 200 — list returned.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_DOCUMENT_LIST: executed after successful retrieval.

## app.routers.document_select module

FastAPI router for document retrieving.

### *async* app.routers.document_select.document_select(request: Request, collection_id: int = Path(PydanticUndefined), document_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [DocumentSelectResponse](app.schemas.md#app.schemas.document_select.DocumentSelectResponse)

Retrieve a single document by ID within a given collection and
return its details, including creator, parent collection, timestamps,
flagged status, filename, size, MIME type, checksum, summary, and
latest revision.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Response schema:**
- DocumentSelectResponse — includes document ID; creator; parent
collection; creation and last-update timestamps (Unix seconds, UTC);
flagged status; filename; file size; MIME type (optional); content
checksum; optional summary; and the latest revision number.

**Path parameters:**
- collection_id (integer ≥ 1): parent collection identifier.
- document_id (integer ≥ 1): document identifier.

**Response codes:**
- 200 — document found; details returned.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — collection or document not found.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_DOCUMENT_SELECT: executed after a successful
retrieval.

## app.routers.document_update module

FastAPI router for document changing.

### *async* app.routers.document_update.document_update(request: Request, schema: [DocumentUpdateRequest](app.schemas.md#app.schemas.document_update.DocumentUpdateRequest), collection_id: int = Path(PydanticUndefined), document_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_edit)) → [DocumentUpdateResponse](app.schemas.md#app.schemas.document_update.DocumentUpdateResponse)

Updates a document by renaming its head file within the current
collection, moving the head file to a different collection (keeping
its name), and/or changing the document summary. Disk changes are
performed with an atomic rename; the document row is staged
(no-commit), the file is renamed or moved on disk, and then the
transaction is committed to keep database and filesystem in sync.

Concurrency is controlled with per-path locks. For rename/move, two
locks are acquired in a deterministic order to prevent deadlocks.
All database and filesystem checks are executed inside this critical
section. These locks are in-process.

Files are stored under their collection directory. The database
enforces uniqueness of (collection_id, filename) for documents.

**Authentication:**
- Requires a valid bearer token with editor role or higher.

**Validation schemas:**
- DocumentUpdateRequest — optional fields: filename, summary,
collection_id.
- DocumentUpdateResponse — returns document_id and
latest_revision_number.

**Path parameters:**
- collection_id (integer ≥ 1) — current collection identifier.
- document_id (integer ≥ 1) — document identifier.

**Request body:**
- application/json with any of: filename, summary,
collection_id.

**Response codes:**
- 200 — update successful.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — collection or document not found.
- 409 — conflict: name already exists in DB/FS or DB/FS mismatch
(document present but file missing, or vice versa).
- 422 — invalid file name.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_DOCUMENT_UPDATE — executed after a successful update.

## app.routers.document_upload module

FastAPI router for file uploading.

### *async* app.routers.document_upload.document_upload(request: Request, collection_id: int = Path(PydanticUndefined), file: UploadFile = File(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_write)) → [DocumentUploadResponse](app.schemas.md#app.schemas.document_upload.DocumentUploadResponse)

Uploads a file into the target collection. If no document with that
name exists, a new one is created; if it does, the current head file
is snapshotted as a new immutable revision and the upload becomes
the new head. File metadata (size, MIME type, checksum) is computed
from the uploaded content and persisted. Disk writes are performed
via a temporary file followed by an atomic rename to avoid partial
states.

This operation is serialized per (collection_id, filename) using an
in-process asyncio lock, so concurrent uploads of the same name in a
single process are executed one by one. In the update path, if the
database commit fails after the head file was already replaced on
disk, the previous head is restored from the just-created revision
to keep the filesystem and database consistent. Thumbnails are
regenerated for image types inside the same critical section after
a successful commit; any outdated thumbnail is removed first.

**Authentication:**
- Requires a valid bearer token with writer role or higher.

**Validation schemas:**
- DocumentUploadResponse — contains the newly created (or updated)
document ID and the latest revision number.

**Path parameters:**
- collection_id (integer ≥ 1) — target collection identifier.

**Request body:**
- file — the file to upload (multipart/form-data).

**Response codes:**
- 201 — file successfully uploaded; document created or replaced
(revision recorded when replaced); thumbnail generated or skipped.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role to perform the operation, invalid JTI,
user is inactive or suspended.
- 404 — collection not found.
- 409 — conflict on DB/FS mismatch for the file (document present
but file missing, or vice versa; MIME type changed for an existing
file).
- 422 — invalid file name.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_DOCUMENT_UPLOAD: executed after a successful upload.

## app.routers.thumbnail_retrieve module

FastAPI router for thumbnail retrieving.

### *async* app.routers.thumbnail_retrieve.thumbnail_retrieve(request: Request, collection_id: int = Path(PydanticUndefined), document_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read))

Retrieve a document’s thumbnail and return raw image bytes. The
image is fetched from the LRU cache first; on miss, it is read from
the filesystem, verified against the stored checksum, and cached.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Path parameters:**
- collection_id (integer ≥ 1): parent collection identifier.
- document_id (integer ≥ 1): document identifier.

**Response:**
- Raw binary image.

**Response codes:**
- 200 — thumbnail returned.
- 304 — not modified (ETag matched).
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or

> suspended.
- 404 — collection or document not found, or no thumbnail set.
- 409 — file not found on filesystem or checksum mismatch.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Side effects:**
- Reads from the LRU cache or filesystem and saves the bytes into
the LRU cache on cache miss.

**Hooks:**
- HOOK_AFTER_THUMBNAIL_RETRIEVE: executed after successful
thumbnail retrieval.

## app.routers.token_invalidate module

FastAPI router for invalidating JWT tokens (logout).

### *async* app.routers.token_invalidate.token_invalidate(request: Request, session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [TokenInvalidateResponse](app.schemas.md#app.schemas.token_invalidate.TokenInvalidateResponse)

Invalidates the current JWT (logout) by rotating the stored JTI for
the authenticated user. On success, persists the new JTI, triggers
the post-invalidate hook, and returns the user ID. The user will
need to authenticate again to obtain a new valid token.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Validation schemas:**
- TokenInvalidateResponse — confirms logout by returning the user
ID.

**Request body / parameters:**
- None.

**Response codes:**
- 200 — token invalidated; logout successful.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_TOKEN_INVALIDATE: executes after successful token
invalidation.

## app.routers.token_retrieve module

FastAPI router for issuing JWT tokens (authentication step 2).

### *async* app.routers.token_retrieve.token_retrieve(request: Request, schema: [TokenRetrieveRequest](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveRequest), session=Depends(get_session), cache=Depends(get_cache)) → [TokenRetrieveResponse](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveResponse)

Completes MFA authentication and issues a JWT access token. Verifies
the username and the provided time-based one-time password (TOTP).
On success, resets the attempt counter, clears the password
acceptance flag, triggers the post-token hook, and returns the user
ID with a signed JWT. On failure, increments attempts and may force
the user to restart authentication from the login step.

**Authentication:**
- Requires successful password authentication (previous login step).

**Validation schemas:**
- TokenRetrieveRequest — request body with username, TOTP, and
optional token expiration.
- TokenRetrieveResponse — contains user ID and JWT token.

**Request body**:
- username (string) — login identifier; automatically trimmed
and lowercased; only Latin letters, digits, and underscore allowed.
- totp (string) — one-time password generated from the MFA secret.
- exp (integer) — custom expiration time in seconds for
the issued JWT.

**Response codes:**
- 200 — TOTP validated; token successfully issued.
- 422 — invalid username, inactive user, user not logged in, or
invalid TOTP.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_TOKEN_RETRIEVE: executes after successful token
retrieval.

## app.routers.user_delete module

FastAPI router for deleting user accounts.

### *async* app.routers.user_delete.user_delete(request: Request, user_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_admin)) → [UserDeleteResponse](app.schemas.md#app.schemas.user_delete.UserDeleteResponse)

Deletes a user account by ID. The current user cannot delete their
own account. The user to delete should not have any relationships
with other app objects.

**Authentication:**
- Requires a valid bearer token with the admin role.

**Validation schemas:**
- UserDeleteResponse — confirmation response with the deleted
user’s ID.

**Path parameters:**
- user_id (integer) — unique identifier of the user to delete.

**Response codes:**
- 200 — user successfully deleted.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — user not found.
- 422 — attempted to delete own account or deletion failed.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_USER_DELETE: executes after successful deletion.

## app.routers.user_list module

### *async* app.routers.user_list.user_list(request: Request, schema=Depends(UserListRequest), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [UserListResponse](app.schemas.md#app.schemas.user_list.UserListResponse)

Retrieves a paginated list of users with optional filters and ordering.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Validation schemas:**
- UserListRequest — pagination, ordering, and optional filters.
- UserListResponse — list of users and total count.

**Query parameters:**
- Mapped from UserListRequest fields (offset, limit, order_by,
order, and optional filter fields).

**Response codes:**
- 200 — list successfully retrieved.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_USER_LIST: executes after the list is retrieved.

## app.routers.user_login module

FastAPI router for user login (authentication step 1).

### *async* app.routers.user_login.user_login(request: Request, schema: [UserLoginRequest](app.schemas.md#app.schemas.user_login.UserLoginRequest), session=Depends(get_session), cache=Depends(get_cache)) → [UserLoginResponse](app.schemas.md#app.schemas.user_login.UserLoginResponse)

Authenticates a user. Verifies credentials and denies access for
suspended or inactive accounts. On success, clears suspension,
resets the attempt counter, triggers the post-login hook, and
returns the user ID with a password acceptance flag; on failure,
increments attempts and may apply a temporary suspension.

**Authentication:**
- No prior authentication required.

**Validation schemas:**
- UserLoginRequest — request body with username and password.
- UserLoginResponse — contains user ID and password acceptance
flag.

**Request body**:
- username (string) — login identifier; automatically trimmed
and lowercased; only Latin letters, digits, and underscore allowed.
- password (string) — login credential.

**Response codes:**
- 200 — user successfully authenticated (password accepted).
- 422 — invalid credentials; user suspended; user inactive.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_USER_LOGIN: executes after successful authentication.

## app.routers.user_password module

FastAPI router for changing user password.

### *async* app.routers.user_password.user_password(request: Request, schema: [UserPasswordRequest](app.schemas.md#app.schemas.user_password.UserPasswordRequest), user_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [UserPasswordResponse](app.schemas.md#app.schemas.user_password.UserPasswordResponse)

Changes the password for the authenticated user. The path user ID
must match the current user, and the new password must differ from
the current password.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Validation schemas:**
- UserPasswordRequest — current and new passwords (new password
must satisfy complexity rules).
- UserPasswordResponse — confirmation with user ID.

**Path parameters:**
- user_id (integer) — ID of the user whose password is updated
(must equal the authenticated user’s ID).

**Response codes:**
- 200 — password successfully changed.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 422 — path user ID mismatch, current password invalid, or new

> password equals the current one.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_USER_PASSWORD: executes after password change.

## app.routers.user_register module

FastAPI router for user registration.

### *async* app.routers.user_register.user_register(request: Request, schema: [UserRegisterRequest](app.schemas.md#app.schemas.user_register.UserRegisterRequest), session=Depends(get_session), cache=Depends(get_cache)) → [UserRegisterResponse](app.schemas.md#app.schemas.user_register.UserRegisterResponse)

Registers a new user. Checks if the username is unique, and creates
a new user with the provided details and credentials. If this is the
first registered user, they are active and get the admin role;
otherwise created as inactive reader and should be activated by
an admin. On success triggers the post-register hook, and returns
the user ID and one-time MFA secret.

**Authentication:**
- No prior authentication required.

**Validation schemas:**
- UserRegisterRequest — request body with username, password,
first name, last name, and optional summary.
- UserRegisterResponse — contains newly registered user ID and
one-time MFA secret.

**Request body**:
- username (string, 2-40) — login identifier; automatically
trimmed and lowercased; only Latin letters, digits, and underscore
allowed.
- password (string, ≥6) — login credential; must meet complexity
rules — uppercase, lowercase, digit, special character; no
whitespace.
- first_name (string, 1-40) — given first name for the user
profile; accepts any characters.
- last_name (string, 1-40) — given name for the user profile;
accepts any characters.
- summary (string, ≤4096, optional) — profile description; accepts
any characters.

**Response codes:**
- 201 — user successfully created.
- 422 — validation failed or username already exists.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_USER_REGISTER: Executes after the user is
successfully created.

## app.routers.user_role module

FastAPI router for managing user roles and active status.

### *async* app.routers.user_role.user_role(request: Request, schema: [UserRoleRequest](app.schemas.md#app.schemas.user_role.UserRoleRequest), user_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_admin)) → [UserRoleResponse](app.schemas.md#app.schemas.user_role.UserRoleResponse)

Changes the role and active status of a specific user account.
The current user cannot update their own role or activity status.

**Authentication:**
- Requires a valid bearer token with the admin role.

**Validation schemas:**
- UserRoleRequest — request body containing the new role and
active status values.
- UserRoleResponse — confirmation response with the affected
user’s ID.

**Path parameters:**
- user_id (integer) — unique identifier of the user whose role or
status should be updated.

**Response codes:**
- 200 — user role or active status successfully updated.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — user not found.
- 422 — attempted to change own role or active status.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_USER_ROLE: executes after the user role or active

> status has been updated.

## app.routers.user_select module

FastAPI router for retrieving user details.

### *async* app.routers.user_select.user_select(request: Request, user_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [UserSelectResponse](app.schemas.md#app.schemas.user_select.UserSelectResponse)

Retrieves a single user by ID and returns their details.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Validation schemas:**
- UserSelectResponse — user details: ID, account creation and
last-login times, role, active status, username, first and last
name, optional summary.

**Path parameters:**
- user_id (integer) — unique user identifier.

**Response codes:**
- 200 — user found; details returned.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — user not found.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_USER_SELECT: executes after successful retrieval.

## app.routers.user_update module

FastAPI router for updating user profile.

### *async* app.routers.user_update.user_update(request: Request, schema: [UserUpdateRequest](app.schemas.md#app.schemas.user_update.UserUpdateRequest), user_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [UserUpdateResponse](app.schemas.md#app.schemas.user_update.UserUpdateResponse)

Updates the authenticated user’s profile details (first and last
names and optional summary). The path user ID must match the current
user.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Validation schemas:**
- UserUpdateRequest — first name, last name, optional summary.
- UserUpdateResponse — confirmation with user ID.

**Path parameters:**
- user_id (integer) — ID of the user whose profile is updated
(must equal the authenticated user’s ID).

**Response codes:**
- 200 — profile successfully updated.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 422 — path user ID mismatch.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_USER_UPDATE: executes after profile update.

## app.routers.userpic_delete module

FastAPI router for deleting user image.

### *async* app.routers.userpic_delete.userpic_delete(request: Request, user_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [UserpicDeleteResponse](app.schemas.md#app.schemas.userpic_delete.UserpicDeleteResponse)

Delete the current user’s userpic and return the user ID. Only the
owner can delete their own userpic.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Validation schemas:**
- UserpicDeleteResponse — contains the user ID.

**Path parameters:**
- user_id (integer): target user ID; must equal the authenticated
user’s ID.

**Response codes:**
- 200 — userpic successfully deleted.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — userpic not found for the user.
- 422 — user ID does not match the authenticated user.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Side effects:**
- Evicts the thumbnail from the in-memory LRU cache.
- Deletes the file at thumbnails/<filename>.

**Hooks:**
- HOOK_AFTER_USERPIC_DELETE: executed after successful userpic
deletion.

## app.routers.userpic_retrieve module

FastAPI router for userpic retrieving.

### *async* app.routers.userpic_retrieve.userpic_retrieve(request: Request, user_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read))

Retrieve a user’s current userpic and return raw image bytes. The
image bytes are fetched from the LRU cache first, and if absent,
read from the filesystem and cached.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Path parameters:**
- user_id (integer ≥ 1): target user identifier.

**Response:**
- Raw binary image.

**Response codes:**
- 200 — userpic returned.
- 304 — not modified (ETag matched).
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 404 — user not found, or no userpic set.
- 409 — file not found on filesystem or checksum mismatch.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Side effects:**
- Reads the image from the LRU cache or filesystem and saves it

> into the LRU cache on cache miss.

**Hooks:**
- HOOK_AFTER_USERPIC_RETRIEVE: executed after successful userpic
retrieval.

## app.routers.userpic_upload module

FastAPI router for uploading userpics.

### *async* app.routers.userpic_upload.userpic_upload(request: Request, file: UploadFile = File(PydanticUndefined), user_id: int = Path(PydanticUndefined), session=Depends(get_session), cache=Depends(get_cache), current_user: [User](app.models.md#app.models.user.User) = Depends(_can_read)) → [UserpicUploadResponse](app.schemas.md#app.schemas.userpic_upload.UserpicUploadResponse)

Uploads a userpic for the authenticated user. The path user ID must
match the current user. The file must be a standard raster image
(JPEG, PNG, GIF, BMP, TIFF, ICO, PBM/PGM/PPM) and will be resized
and re-encoded to JPEG; on success, any previous thumbnail is
deleted and the new image is saved at the configured dimensions
and quality.

**Authentication:**
- Requires a valid bearer token with reader role or higher.

**Validation schemas:**
- UserpicUploadResponse — confirmation with the user ID.

**Path parameters:**
- user_id (integer) — identifier of the user uploading the image.

**Request body:**
- file (multipart/form-data) — image to upload; content type must
be in the configured image MIME allowlist.

**Response codes:**
- 200 — userpic successfully uploaded and stored.
- 401 — missing, invalid, or expired token.
- 403 — insufficient role, invalid JTI, user is inactive or
suspended.
- 422 — path user ID does not match current user or file mimetype
is invalid.
- 423 — application is temporarily locked.
- 498 — secret key is missing.
- 499 — secret key is invalid.

**Hooks:**
- HOOK_AFTER_USERPIC_UPLOAD: executes after the image is processed
and saved.

## Module contents
