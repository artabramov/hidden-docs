# app.models package

## Submodules

## app.models.collection module

SQLAlchemy model for collections.

### *class* app.models.collection.Collection(user_id, readonly, name, summary=None)

Bases: [`Base`](app.md#app.sqlite.Base)

SQLAlchemy model for collections. Stores a unique name, read-only
flag, creation/update timestamps, and optional summary.

#### collection_documents

#### collection_meta

#### collection_user

#### created_date

#### id

#### name

#### path(config: Any) → str

Return absolute path to the collection by config.

#### *classmethod* path_for_dir(config: Any, collection_name: str) → str

Return absolute path to the collection by parameters.

#### readonly

#### summary

#### *async* to_dict() → dict

Returns a dictionary representation of the collection.

#### updated_date

#### user_id

## app.models.collection_meta module

SQLAlchemy model for collection metadata.

### *class* app.models.collection_meta.CollectionMeta(\*\*kwargs)

Bases: [`Base`](app.md#app.sqlite.Base)

SQLAlchemy model for collection metadata. Stores a key-value pair
linked to a collection; keys are unique within each collection.

#### collection_id

#### created_date

#### id

#### meta_collection

#### meta_key

#### meta_value

#### updated_date

## app.models.document module

SQLAlchemy model for documents.

### *class* app.models.document.Document(user_id, collection_id, filename, filesize, checksum, mimetype=None, flagged=False, summary=None, latest_revision_number=0)

Bases: [`Base`](app.md#app.sqlite.Base)

#### checksum

#### collection_id

#### created_date

#### document_collection

#### document_meta

#### document_revisions

#### document_tags

#### document_thumbnail

#### document_user

#### filename

#### filesize

#### flagged

#### *property* has_revisions *: bool*

#### *property* has_thumbnail *: bool*

#### id

#### latest_revision_number

#### mimetype

#### path(config: Any) → str

Return absolute path to the document file by config.

#### *classmethod* path_for_filename(config: Any, collection_name: str, filename: str) → str

Return absolute path to the document file by parameters.

#### summary

#### *async* to_dict() → dict

Returns a dictionary representation of the document.

#### updated_date

#### user_id

## app.models.document_meta module

SQLAlchemy model for document metadata.

### *class* app.models.document_meta.DocumentMeta(\*\*kwargs)

Bases: [`Base`](app.md#app.sqlite.Base)

SQLAlchemy model for document metadata. Stores a key-value pair
linked to a document; keys are unique within each document.

#### created_date

#### document_id

#### id

#### meta_document

#### meta_key

#### meta_value

#### updated_date

## app.models.document_revision module

SQLAlchemy model for document revisions.

### *class* app.models.document_revision.DocumentRevision(user_id, document_id, revision_number, uuid, filesize, checksum)

Bases: [`Base`](app.md#app.sqlite.Base)

SQLAlchemy model for document revisions.
Immutable snapshots of a document.

#### checksum

#### created_date

#### document_id

#### filesize

#### id

#### path(config: Any) → str

Return absolute path to the thumbnail file by its UUID.

#### *classmethod* path_for_uuid(config: Any, uuid: str) → str

Return absolute path for a given UUID using config.

#### revision_document

#### revision_number

#### revision_user

#### *async* to_dict() → dict

Returns a dictionary representation of the revision.

#### user_id

#### uuid

## app.models.document_tag module

SQLAlchemy model for document tags.

### *class* app.models.document_tag.DocumentTag(\*\*kwargs)

Bases: [`Base`](app.md#app.sqlite.Base)

SQLAlchemy model for document tags. Stores a tag value linked
to a document; values are unique within each document.

#### created_date

#### document_id

#### id

#### tag_document

#### tag_value

## app.models.document_thumbnail module

SQLAlchemy model for document thumbnails.

### *class* app.models.document_thumbnail.DocumentThumbnail(document_id, uuid, filesize, checksum)

Bases: [`Base`](app.md#app.sqlite.Base), [`ThumbnailMixin`](app.helpers.md#app.helpers.thumbnail_mixin.ThumbnailMixin)

SQLAlchemy model for document thumbnails. One-to-one thumbnail
linked to a document; stores UUID (thumbnail file name), file
size, and checksum.

#### checksum

#### created_date

#### document_id

#### filesize

#### id

#### thumbnail_document

#### updated_date

#### uuid

## app.models.user module

SQLAlchemy model for users.

### *class* app.models.user.User(username, password_hash, first_name, last_name, role, active, mfa_secret_encrypted, jti_encrypted, summary=None)

Bases: [`Base`](app.md#app.sqlite.Base)

SQLAlchemy model for users. Stores authentication credentials,
access role, status flags, audit timestamps, MFA fields, and
optional profile information.

#### active

#### *property* can_admin *: bool*

#### *property* can_edit *: bool*

#### *property* can_read *: bool*

#### *property* can_write *: bool*

#### created_date

#### first_name

#### full_name

#### *property* has_thumbnail *: bool*

#### id

#### jti_encrypted

#### last_login_date

#### last_name

#### mfa_attempts

#### mfa_secret_encrypted

#### password_accepted

#### password_attempts

#### password_hash

#### role

#### summary

#### suspended_until_date

#### *async* to_dict() → dict

Returns a dictionary representation of the user.

#### updated_date

#### user_collections

#### user_documents

#### user_meta

#### user_revisions

#### user_thumbnail

#### username

### *class* app.models.user.UserRole

Bases: `object`

Defines the available user roles in the application.
Each role determines a predefined set of permissions.

#### admin *= 'admin'*

#### editor *= 'editor'*

#### reader *= 'reader'*

#### writer *= 'writer'*

## app.models.user_meta module

SQLAlchemy model for user metadata.

### *class* app.models.user_meta.UserMeta(\*\*kwargs)

Bases: [`Base`](app.md#app.sqlite.Base)

SQLAlchemy model for user metadata. Stores a key-value pair
linked to a user; keys are unique within each collection.

#### created_date

#### id

#### meta_key

#### meta_user

#### meta_value

#### updated_date

#### user_id

## app.models.user_thumbnail module

SQLAlchemy model for user thumbnails.

### *class* app.models.user_thumbnail.UserThumbnail(user_id, uuid, filesize, checksum)

Bases: [`Base`](app.md#app.sqlite.Base), [`ThumbnailMixin`](app.helpers.md#app.helpers.thumbnail_mixin.ThumbnailMixin)

SQLAlchemy model for user thumbnails. One-to-one thumbnail
linked to a user; stores its UUID, size, and checksum.

#### checksum

#### created_date

#### filesize

#### id

#### thumbnail_user

#### updated_date

#### user_id

#### uuid

## Module contents
