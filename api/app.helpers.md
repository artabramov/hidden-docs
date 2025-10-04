# app.helpers package

## Submodules

## app.helpers.image_helper module

Helper for image operations.

### *async* app.helpers.image_helper.image_resize(path: str, width: int, height: int, quality: int)

Asynchronously runs the sync resizer in a worker thread: applies
EXIF orientation, center-crops to the target aspect ratio, resizes
with Lanczos, and overwrites the file as a progressive JPEG.

## app.helpers.jwt_helper module

Helpers for JSON Web Tokens (JWT): generate a JTI, build a user payload,
and encode/decode JWTs via PyJWT.

### app.helpers.jwt_helper.create_payload(user: [User](app.models.md#app.models.user.User), jti: str, exp: int = None)

Builds a JWT claims payload for the given user including user_id,
role, username, jti, and iat (Unix seconds); if exp is provided it
is used as an absolute expiration timestamp, otherwise the payload
is created without an exp claim.

### app.helpers.jwt_helper.decode_jwt(jwt_token: str, jwt_secret: str, jwt_algorithms: list) → dict

Decodes a JWT using the given secret and allowed algorithms,
validating the signature and standard claims (such as exp and iat)
and returning the claims dictionary, raising PyJWT exceptions on
invalid or expired tokens.

### app.helpers.jwt_helper.encode_jwt(payload: dict, jwt_secret: str, jwt_algorithm: str) → str

Encodes and signs the given claims payload into a compact JWT using
the supplied secret and algorithm via PyJWT.

### app.helpers.jwt_helper.generate_jti(key_length: int) → str

Generates a cryptographically random alphanumeric JTI of the given
length for uniquely identifying and potentially revoking tokens.

## app.helpers.mfa_helper module

Provides a helper to generate a random Base32-encoded secret for
time-based one-time password (TOTP) multi-factor authentication (MFA).

### app.helpers.mfa_helper.calculate_totp(mfa_secret: str)

Computes the current time-based one-time password derived from
the provided Base32 secret, compatible with standard TOTP apps.

### app.helpers.mfa_helper.generate_mfa_secret() → str

Generates and returns a random base32-encoded secret suitable
for use with time-based one-time password (TOTP) MFA systems.

## app.helpers.thumbnail_mixin module

### *class* app.helpers.thumbnail_mixin.ThumbnailMixin

Bases: `object`

Build absolute paths to thumbnail files.

#### path(config: Any) → str

Return absolute path to the thumbnail file by its UUID.

#### *classmethod* path_for_uuid(config: Any, uuid: str) → str

Return absolute path for a given UUID using config.

## Module contents
