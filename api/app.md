# app package

## Subpackages

* [app.helpers package](app.helpers.md)
  * [Submodules](app.helpers.md#submodules)
  * [app.helpers.image_helper module](app.helpers.md#module-app.helpers.image_helper)
    * [`image_resize()`](app.helpers.md#app.helpers.image_helper.image_resize)
  * [app.helpers.jwt_helper module](app.helpers.md#module-app.helpers.jwt_helper)
    * [`create_payload()`](app.helpers.md#app.helpers.jwt_helper.create_payload)
    * [`decode_jwt()`](app.helpers.md#app.helpers.jwt_helper.decode_jwt)
    * [`encode_jwt()`](app.helpers.md#app.helpers.jwt_helper.encode_jwt)
    * [`generate_jti()`](app.helpers.md#app.helpers.jwt_helper.generate_jti)
  * [app.helpers.mfa_helper module](app.helpers.md#module-app.helpers.mfa_helper)
    * [`calculate_totp()`](app.helpers.md#app.helpers.mfa_helper.calculate_totp)
    * [`generate_mfa_secret()`](app.helpers.md#app.helpers.mfa_helper.generate_mfa_secret)
  * [app.helpers.thumbnail_mixin module](app.helpers.md#module-app.helpers.thumbnail_mixin)
    * [`ThumbnailMixin`](app.helpers.md#app.helpers.thumbnail_mixin.ThumbnailMixin)
      * [`ThumbnailMixin.path()`](app.helpers.md#app.helpers.thumbnail_mixin.ThumbnailMixin.path)
      * [`ThumbnailMixin.path_for_uuid()`](app.helpers.md#app.helpers.thumbnail_mixin.ThumbnailMixin.path_for_uuid)
  * [Module contents](app.helpers.md#module-app.helpers)
* [app.models package](app.models.md)
  * [Submodules](app.models.md#submodules)
  * [app.models.collection module](app.models.md#module-app.models.collection)
    * [`Collection`](app.models.md#app.models.collection.Collection)
      * [`Collection.collection_documents`](app.models.md#app.models.collection.Collection.collection_documents)
      * [`Collection.collection_meta`](app.models.md#app.models.collection.Collection.collection_meta)
      * [`Collection.collection_user`](app.models.md#app.models.collection.Collection.collection_user)
      * [`Collection.created_date`](app.models.md#app.models.collection.Collection.created_date)
      * [`Collection.id`](app.models.md#app.models.collection.Collection.id)
      * [`Collection.name`](app.models.md#app.models.collection.Collection.name)
      * [`Collection.path()`](app.models.md#app.models.collection.Collection.path)
      * [`Collection.path_for_dir()`](app.models.md#app.models.collection.Collection.path_for_dir)
      * [`Collection.readonly`](app.models.md#app.models.collection.Collection.readonly)
      * [`Collection.summary`](app.models.md#app.models.collection.Collection.summary)
      * [`Collection.to_dict()`](app.models.md#app.models.collection.Collection.to_dict)
      * [`Collection.updated_date`](app.models.md#app.models.collection.Collection.updated_date)
      * [`Collection.user_id`](app.models.md#app.models.collection.Collection.user_id)
  * [app.models.collection_meta module](app.models.md#module-app.models.collection_meta)
    * [`CollectionMeta`](app.models.md#app.models.collection_meta.CollectionMeta)
      * [`CollectionMeta.collection_id`](app.models.md#app.models.collection_meta.CollectionMeta.collection_id)
      * [`CollectionMeta.created_date`](app.models.md#app.models.collection_meta.CollectionMeta.created_date)
      * [`CollectionMeta.id`](app.models.md#app.models.collection_meta.CollectionMeta.id)
      * [`CollectionMeta.meta_collection`](app.models.md#app.models.collection_meta.CollectionMeta.meta_collection)
      * [`CollectionMeta.meta_key`](app.models.md#app.models.collection_meta.CollectionMeta.meta_key)
      * [`CollectionMeta.meta_value`](app.models.md#app.models.collection_meta.CollectionMeta.meta_value)
      * [`CollectionMeta.updated_date`](app.models.md#app.models.collection_meta.CollectionMeta.updated_date)
  * [app.models.document module](app.models.md#module-app.models.document)
    * [`Document`](app.models.md#app.models.document.Document)
      * [`Document.checksum`](app.models.md#app.models.document.Document.checksum)
      * [`Document.collection_id`](app.models.md#app.models.document.Document.collection_id)
      * [`Document.created_date`](app.models.md#app.models.document.Document.created_date)
      * [`Document.document_collection`](app.models.md#app.models.document.Document.document_collection)
      * [`Document.document_meta`](app.models.md#app.models.document.Document.document_meta)
      * [`Document.document_revisions`](app.models.md#app.models.document.Document.document_revisions)
      * [`Document.document_tags`](app.models.md#app.models.document.Document.document_tags)
      * [`Document.document_thumbnail`](app.models.md#app.models.document.Document.document_thumbnail)
      * [`Document.document_user`](app.models.md#app.models.document.Document.document_user)
      * [`Document.filename`](app.models.md#app.models.document.Document.filename)
      * [`Document.filesize`](app.models.md#app.models.document.Document.filesize)
      * [`Document.flagged`](app.models.md#app.models.document.Document.flagged)
      * [`Document.has_revisions`](app.models.md#app.models.document.Document.has_revisions)
      * [`Document.has_thumbnail`](app.models.md#app.models.document.Document.has_thumbnail)
      * [`Document.id`](app.models.md#app.models.document.Document.id)
      * [`Document.latest_revision_number`](app.models.md#app.models.document.Document.latest_revision_number)
      * [`Document.mimetype`](app.models.md#app.models.document.Document.mimetype)
      * [`Document.path()`](app.models.md#app.models.document.Document.path)
      * [`Document.path_for_filename()`](app.models.md#app.models.document.Document.path_for_filename)
      * [`Document.summary`](app.models.md#app.models.document.Document.summary)
      * [`Document.to_dict()`](app.models.md#app.models.document.Document.to_dict)
      * [`Document.updated_date`](app.models.md#app.models.document.Document.updated_date)
      * [`Document.user_id`](app.models.md#app.models.document.Document.user_id)
  * [app.models.document_meta module](app.models.md#module-app.models.document_meta)
    * [`DocumentMeta`](app.models.md#app.models.document_meta.DocumentMeta)
      * [`DocumentMeta.created_date`](app.models.md#app.models.document_meta.DocumentMeta.created_date)
      * [`DocumentMeta.document_id`](app.models.md#app.models.document_meta.DocumentMeta.document_id)
      * [`DocumentMeta.id`](app.models.md#app.models.document_meta.DocumentMeta.id)
      * [`DocumentMeta.meta_document`](app.models.md#app.models.document_meta.DocumentMeta.meta_document)
      * [`DocumentMeta.meta_key`](app.models.md#app.models.document_meta.DocumentMeta.meta_key)
      * [`DocumentMeta.meta_value`](app.models.md#app.models.document_meta.DocumentMeta.meta_value)
      * [`DocumentMeta.updated_date`](app.models.md#app.models.document_meta.DocumentMeta.updated_date)
  * [app.models.document_revision module](app.models.md#module-app.models.document_revision)
    * [`DocumentRevision`](app.models.md#app.models.document_revision.DocumentRevision)
      * [`DocumentRevision.checksum`](app.models.md#app.models.document_revision.DocumentRevision.checksum)
      * [`DocumentRevision.created_date`](app.models.md#app.models.document_revision.DocumentRevision.created_date)
      * [`DocumentRevision.document_id`](app.models.md#app.models.document_revision.DocumentRevision.document_id)
      * [`DocumentRevision.filesize`](app.models.md#app.models.document_revision.DocumentRevision.filesize)
      * [`DocumentRevision.id`](app.models.md#app.models.document_revision.DocumentRevision.id)
      * [`DocumentRevision.path()`](app.models.md#app.models.document_revision.DocumentRevision.path)
      * [`DocumentRevision.path_for_uuid()`](app.models.md#app.models.document_revision.DocumentRevision.path_for_uuid)
      * [`DocumentRevision.revision_document`](app.models.md#app.models.document_revision.DocumentRevision.revision_document)
      * [`DocumentRevision.revision_number`](app.models.md#app.models.document_revision.DocumentRevision.revision_number)
      * [`DocumentRevision.revision_user`](app.models.md#app.models.document_revision.DocumentRevision.revision_user)
      * [`DocumentRevision.to_dict()`](app.models.md#app.models.document_revision.DocumentRevision.to_dict)
      * [`DocumentRevision.user_id`](app.models.md#app.models.document_revision.DocumentRevision.user_id)
      * [`DocumentRevision.uuid`](app.models.md#app.models.document_revision.DocumentRevision.uuid)
  * [app.models.document_tag module](app.models.md#module-app.models.document_tag)
    * [`DocumentTag`](app.models.md#app.models.document_tag.DocumentTag)
      * [`DocumentTag.created_date`](app.models.md#app.models.document_tag.DocumentTag.created_date)
      * [`DocumentTag.document_id`](app.models.md#app.models.document_tag.DocumentTag.document_id)
      * [`DocumentTag.id`](app.models.md#app.models.document_tag.DocumentTag.id)
      * [`DocumentTag.tag_document`](app.models.md#app.models.document_tag.DocumentTag.tag_document)
      * [`DocumentTag.tag_value`](app.models.md#app.models.document_tag.DocumentTag.tag_value)
  * [app.models.document_thumbnail module](app.models.md#module-app.models.document_thumbnail)
    * [`DocumentThumbnail`](app.models.md#app.models.document_thumbnail.DocumentThumbnail)
      * [`DocumentThumbnail.checksum`](app.models.md#app.models.document_thumbnail.DocumentThumbnail.checksum)
      * [`DocumentThumbnail.created_date`](app.models.md#app.models.document_thumbnail.DocumentThumbnail.created_date)
      * [`DocumentThumbnail.document_id`](app.models.md#app.models.document_thumbnail.DocumentThumbnail.document_id)
      * [`DocumentThumbnail.filesize`](app.models.md#app.models.document_thumbnail.DocumentThumbnail.filesize)
      * [`DocumentThumbnail.id`](app.models.md#app.models.document_thumbnail.DocumentThumbnail.id)
      * [`DocumentThumbnail.thumbnail_document`](app.models.md#app.models.document_thumbnail.DocumentThumbnail.thumbnail_document)
      * [`DocumentThumbnail.updated_date`](app.models.md#app.models.document_thumbnail.DocumentThumbnail.updated_date)
      * [`DocumentThumbnail.uuid`](app.models.md#app.models.document_thumbnail.DocumentThumbnail.uuid)
  * [app.models.user module](app.models.md#module-app.models.user)
    * [`User`](app.models.md#app.models.user.User)
      * [`User.active`](app.models.md#app.models.user.User.active)
      * [`User.can_admin`](app.models.md#app.models.user.User.can_admin)
      * [`User.can_edit`](app.models.md#app.models.user.User.can_edit)
      * [`User.can_read`](app.models.md#app.models.user.User.can_read)
      * [`User.can_write`](app.models.md#app.models.user.User.can_write)
      * [`User.created_date`](app.models.md#app.models.user.User.created_date)
      * [`User.first_name`](app.models.md#app.models.user.User.first_name)
      * [`User.full_name`](app.models.md#app.models.user.User.full_name)
      * [`User.has_thumbnail`](app.models.md#app.models.user.User.has_thumbnail)
      * [`User.id`](app.models.md#app.models.user.User.id)
      * [`User.jti_encrypted`](app.models.md#app.models.user.User.jti_encrypted)
      * [`User.last_login_date`](app.models.md#app.models.user.User.last_login_date)
      * [`User.last_name`](app.models.md#app.models.user.User.last_name)
      * [`User.mfa_attempts`](app.models.md#app.models.user.User.mfa_attempts)
      * [`User.mfa_secret_encrypted`](app.models.md#app.models.user.User.mfa_secret_encrypted)
      * [`User.password_accepted`](app.models.md#app.models.user.User.password_accepted)
      * [`User.password_attempts`](app.models.md#app.models.user.User.password_attempts)
      * [`User.password_hash`](app.models.md#app.models.user.User.password_hash)
      * [`User.role`](app.models.md#app.models.user.User.role)
      * [`User.summary`](app.models.md#app.models.user.User.summary)
      * [`User.suspended_until_date`](app.models.md#app.models.user.User.suspended_until_date)
      * [`User.to_dict()`](app.models.md#app.models.user.User.to_dict)
      * [`User.updated_date`](app.models.md#app.models.user.User.updated_date)
      * [`User.user_collections`](app.models.md#app.models.user.User.user_collections)
      * [`User.user_documents`](app.models.md#app.models.user.User.user_documents)
      * [`User.user_meta`](app.models.md#app.models.user.User.user_meta)
      * [`User.user_revisions`](app.models.md#app.models.user.User.user_revisions)
      * [`User.user_thumbnail`](app.models.md#app.models.user.User.user_thumbnail)
      * [`User.username`](app.models.md#app.models.user.User.username)
    * [`UserRole`](app.models.md#app.models.user.UserRole)
      * [`UserRole.admin`](app.models.md#app.models.user.UserRole.admin)
      * [`UserRole.editor`](app.models.md#app.models.user.UserRole.editor)
      * [`UserRole.reader`](app.models.md#app.models.user.UserRole.reader)
      * [`UserRole.writer`](app.models.md#app.models.user.UserRole.writer)
  * [app.models.user_meta module](app.models.md#module-app.models.user_meta)
    * [`UserMeta`](app.models.md#app.models.user_meta.UserMeta)
      * [`UserMeta.created_date`](app.models.md#app.models.user_meta.UserMeta.created_date)
      * [`UserMeta.id`](app.models.md#app.models.user_meta.UserMeta.id)
      * [`UserMeta.meta_key`](app.models.md#app.models.user_meta.UserMeta.meta_key)
      * [`UserMeta.meta_user`](app.models.md#app.models.user_meta.UserMeta.meta_user)
      * [`UserMeta.meta_value`](app.models.md#app.models.user_meta.UserMeta.meta_value)
      * [`UserMeta.updated_date`](app.models.md#app.models.user_meta.UserMeta.updated_date)
      * [`UserMeta.user_id`](app.models.md#app.models.user_meta.UserMeta.user_id)
  * [app.models.user_thumbnail module](app.models.md#module-app.models.user_thumbnail)
    * [`UserThumbnail`](app.models.md#app.models.user_thumbnail.UserThumbnail)
      * [`UserThumbnail.checksum`](app.models.md#app.models.user_thumbnail.UserThumbnail.checksum)
      * [`UserThumbnail.created_date`](app.models.md#app.models.user_thumbnail.UserThumbnail.created_date)
      * [`UserThumbnail.filesize`](app.models.md#app.models.user_thumbnail.UserThumbnail.filesize)
      * [`UserThumbnail.id`](app.models.md#app.models.user_thumbnail.UserThumbnail.id)
      * [`UserThumbnail.thumbnail_user`](app.models.md#app.models.user_thumbnail.UserThumbnail.thumbnail_user)
      * [`UserThumbnail.updated_date`](app.models.md#app.models.user_thumbnail.UserThumbnail.updated_date)
      * [`UserThumbnail.user_id`](app.models.md#app.models.user_thumbnail.UserThumbnail.user_id)
      * [`UserThumbnail.uuid`](app.models.md#app.models.user_thumbnail.UserThumbnail.uuid)
  * [Module contents](app.models.md#module-app.models)
* [app.routers package](app.routers.md)
  * [Submodules](app.routers.md#submodules)
  * [app.routers.collection_delete module](app.routers.md#module-app.routers.collection_delete)
    * [`collection_delete()`](app.routers.md#app.routers.collection_delete.collection_delete)
  * [app.routers.collection_insert module](app.routers.md#module-app.routers.collection_insert)
    * [`collection_insert()`](app.routers.md#app.routers.collection_insert.collection_insert)
  * [app.routers.collection_list module](app.routers.md#module-app.routers.collection_list)
    * [`collection_list()`](app.routers.md#app.routers.collection_list.collection_list)
  * [app.routers.collection_select module](app.routers.md#module-app.routers.collection_select)
    * [`collection_select()`](app.routers.md#app.routers.collection_select.collection_select)
  * [app.routers.collection_update module](app.routers.md#module-app.routers.collection_update)
    * [`collection_update()`](app.routers.md#app.routers.collection_update.collection_update)
  * [app.routers.document_delete module](app.routers.md#module-app.routers.document_delete)
    * [`document_delete()`](app.routers.md#app.routers.document_delete.document_delete)
  * [app.routers.document_download module](app.routers.md#module-app.routers.document_download)
    * [`document_download()`](app.routers.md#app.routers.document_download.document_download)
  * [app.routers.document_list module](app.routers.md#module-app.routers.document_list)
    * [`document_list()`](app.routers.md#app.routers.document_list.document_list)
  * [app.routers.document_select module](app.routers.md#module-app.routers.document_select)
    * [`document_select()`](app.routers.md#app.routers.document_select.document_select)
  * [app.routers.document_update module](app.routers.md#module-app.routers.document_update)
    * [`document_update()`](app.routers.md#app.routers.document_update.document_update)
  * [app.routers.document_upload module](app.routers.md#module-app.routers.document_upload)
    * [`document_upload()`](app.routers.md#app.routers.document_upload.document_upload)
  * [app.routers.thumbnail_retrieve module](app.routers.md#module-app.routers.thumbnail_retrieve)
    * [`thumbnail_retrieve()`](app.routers.md#app.routers.thumbnail_retrieve.thumbnail_retrieve)
  * [app.routers.token_invalidate module](app.routers.md#module-app.routers.token_invalidate)
    * [`token_invalidate()`](app.routers.md#app.routers.token_invalidate.token_invalidate)
  * [app.routers.token_retrieve module](app.routers.md#module-app.routers.token_retrieve)
    * [`token_retrieve()`](app.routers.md#app.routers.token_retrieve.token_retrieve)
  * [app.routers.user_delete module](app.routers.md#module-app.routers.user_delete)
    * [`user_delete()`](app.routers.md#app.routers.user_delete.user_delete)
  * [app.routers.user_list module](app.routers.md#module-app.routers.user_list)
    * [`user_list()`](app.routers.md#app.routers.user_list.user_list)
  * [app.routers.user_login module](app.routers.md#module-app.routers.user_login)
    * [`user_login()`](app.routers.md#app.routers.user_login.user_login)
  * [app.routers.user_password module](app.routers.md#module-app.routers.user_password)
    * [`user_password()`](app.routers.md#app.routers.user_password.user_password)
  * [app.routers.user_register module](app.routers.md#module-app.routers.user_register)
    * [`user_register()`](app.routers.md#app.routers.user_register.user_register)
  * [app.routers.user_role module](app.routers.md#module-app.routers.user_role)
    * [`user_role()`](app.routers.md#app.routers.user_role.user_role)
  * [app.routers.user_select module](app.routers.md#module-app.routers.user_select)
    * [`user_select()`](app.routers.md#app.routers.user_select.user_select)
  * [app.routers.user_update module](app.routers.md#module-app.routers.user_update)
    * [`user_update()`](app.routers.md#app.routers.user_update.user_update)
  * [app.routers.userpic_delete module](app.routers.md#module-app.routers.userpic_delete)
    * [`userpic_delete()`](app.routers.md#app.routers.userpic_delete.userpic_delete)
  * [app.routers.userpic_retrieve module](app.routers.md#module-app.routers.userpic_retrieve)
    * [`userpic_retrieve()`](app.routers.md#app.routers.userpic_retrieve.userpic_retrieve)
  * [app.routers.userpic_upload module](app.routers.md#module-app.routers.userpic_upload)
    * [`userpic_upload()`](app.routers.md#app.routers.userpic_upload.userpic_upload)
  * [Module contents](app.routers.md#module-app.routers)
* [app.schemas package](app.schemas.md)
  * [Submodules](app.schemas.md#submodules)
  * [app.schemas.collection_delete module](app.schemas.md#module-app.schemas.collection_delete)
    * [`CollectionDeleteResponse`](app.schemas.md#app.schemas.collection_delete.CollectionDeleteResponse)
      * [`CollectionDeleteResponse.collection_id`](app.schemas.md#app.schemas.collection_delete.CollectionDeleteResponse.collection_id)
      * [`CollectionDeleteResponse.model_config`](app.schemas.md#app.schemas.collection_delete.CollectionDeleteResponse.model_config)
  * [app.schemas.collection_insert module](app.schemas.md#module-app.schemas.collection_insert)
    * [`CollectionInsertRequest`](app.schemas.md#app.schemas.collection_insert.CollectionInsertRequest)
      * [`CollectionInsertRequest.model_config`](app.schemas.md#app.schemas.collection_insert.CollectionInsertRequest.model_config)
      * [`CollectionInsertRequest.name`](app.schemas.md#app.schemas.collection_insert.CollectionInsertRequest.name)
      * [`CollectionInsertRequest.readonly`](app.schemas.md#app.schemas.collection_insert.CollectionInsertRequest.readonly)
      * [`CollectionInsertRequest.summary`](app.schemas.md#app.schemas.collection_insert.CollectionInsertRequest.summary)
    * [`CollectionInsertResponse`](app.schemas.md#app.schemas.collection_insert.CollectionInsertResponse)
      * [`CollectionInsertResponse.collection_id`](app.schemas.md#app.schemas.collection_insert.CollectionInsertResponse.collection_id)
      * [`CollectionInsertResponse.model_config`](app.schemas.md#app.schemas.collection_insert.CollectionInsertResponse.model_config)
  * [app.schemas.collection_list module](app.schemas.md#module-app.schemas.collection_list)
    * [`CollectionListRequest`](app.schemas.md#app.schemas.collection_list.CollectionListRequest)
      * [`CollectionListRequest.created_date__ge`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.created_date__ge)
      * [`CollectionListRequest.created_date__le`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.created_date__le)
      * [`CollectionListRequest.limit`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.limit)
      * [`CollectionListRequest.model_config`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.model_config)
      * [`CollectionListRequest.name__ilike`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.name__ilike)
      * [`CollectionListRequest.offset`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.offset)
      * [`CollectionListRequest.order`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.order)
      * [`CollectionListRequest.order_by`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.order_by)
      * [`CollectionListRequest.readonly__eq`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.readonly__eq)
      * [`CollectionListRequest.updated_date__ge`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.updated_date__ge)
      * [`CollectionListRequest.updated_date__le`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.updated_date__le)
      * [`CollectionListRequest.user_id__eq`](app.schemas.md#app.schemas.collection_list.CollectionListRequest.user_id__eq)
    * [`CollectionListResponse`](app.schemas.md#app.schemas.collection_list.CollectionListResponse)
      * [`CollectionListResponse.collections`](app.schemas.md#app.schemas.collection_list.CollectionListResponse.collections)
      * [`CollectionListResponse.collections_count`](app.schemas.md#app.schemas.collection_list.CollectionListResponse.collections_count)
      * [`CollectionListResponse.model_config`](app.schemas.md#app.schemas.collection_list.CollectionListResponse.model_config)
  * [app.schemas.collection_select module](app.schemas.md#module-app.schemas.collection_select)
    * [`CollectionSelectResponse`](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse)
      * [`CollectionSelectResponse.created_date`](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse.created_date)
      * [`CollectionSelectResponse.id`](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse.id)
      * [`CollectionSelectResponse.model_config`](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse.model_config)
      * [`CollectionSelectResponse.name`](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse.name)
      * [`CollectionSelectResponse.readonly`](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse.readonly)
      * [`CollectionSelectResponse.summary`](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse.summary)
      * [`CollectionSelectResponse.updated_date`](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse.updated_date)
      * [`CollectionSelectResponse.user`](app.schemas.md#app.schemas.collection_select.CollectionSelectResponse.user)
  * [app.schemas.collection_update module](app.schemas.md#module-app.schemas.collection_update)
    * [`CollectionUpdateRequest`](app.schemas.md#app.schemas.collection_update.CollectionUpdateRequest)
      * [`CollectionUpdateRequest.model_config`](app.schemas.md#app.schemas.collection_update.CollectionUpdateRequest.model_config)
      * [`CollectionUpdateRequest.name`](app.schemas.md#app.schemas.collection_update.CollectionUpdateRequest.name)
      * [`CollectionUpdateRequest.readonly`](app.schemas.md#app.schemas.collection_update.CollectionUpdateRequest.readonly)
      * [`CollectionUpdateRequest.summary`](app.schemas.md#app.schemas.collection_update.CollectionUpdateRequest.summary)
    * [`CollectionUpdateResponse`](app.schemas.md#app.schemas.collection_update.CollectionUpdateResponse)
      * [`CollectionUpdateResponse.collection_id`](app.schemas.md#app.schemas.collection_update.CollectionUpdateResponse.collection_id)
      * [`CollectionUpdateResponse.model_config`](app.schemas.md#app.schemas.collection_update.CollectionUpdateResponse.model_config)
  * [app.schemas.document_delete module](app.schemas.md#module-app.schemas.document_delete)
    * [`DocumentDeleteResponse`](app.schemas.md#app.schemas.document_delete.DocumentDeleteResponse)
      * [`DocumentDeleteResponse.document_id`](app.schemas.md#app.schemas.document_delete.DocumentDeleteResponse.document_id)
      * [`DocumentDeleteResponse.latest_revision_number`](app.schemas.md#app.schemas.document_delete.DocumentDeleteResponse.latest_revision_number)
      * [`DocumentDeleteResponse.model_config`](app.schemas.md#app.schemas.document_delete.DocumentDeleteResponse.model_config)
  * [app.schemas.document_list module](app.schemas.md#module-app.schemas.document_list)
    * [`DocumentListRequest`](app.schemas.md#app.schemas.document_list.DocumentListRequest)
      * [`DocumentListRequest.collection_id__eq`](app.schemas.md#app.schemas.document_list.DocumentListRequest.collection_id__eq)
      * [`DocumentListRequest.created_date__ge`](app.schemas.md#app.schemas.document_list.DocumentListRequest.created_date__ge)
      * [`DocumentListRequest.created_date__le`](app.schemas.md#app.schemas.document_list.DocumentListRequest.created_date__le)
      * [`DocumentListRequest.filename__ilike`](app.schemas.md#app.schemas.document_list.DocumentListRequest.filename__ilike)
      * [`DocumentListRequest.filesize__ge`](app.schemas.md#app.schemas.document_list.DocumentListRequest.filesize__ge)
      * [`DocumentListRequest.filesize__le`](app.schemas.md#app.schemas.document_list.DocumentListRequest.filesize__le)
      * [`DocumentListRequest.flagged__eq`](app.schemas.md#app.schemas.document_list.DocumentListRequest.flagged__eq)
      * [`DocumentListRequest.limit`](app.schemas.md#app.schemas.document_list.DocumentListRequest.limit)
      * [`DocumentListRequest.mimetype__ilike`](app.schemas.md#app.schemas.document_list.DocumentListRequest.mimetype__ilike)
      * [`DocumentListRequest.model_config`](app.schemas.md#app.schemas.document_list.DocumentListRequest.model_config)
      * [`DocumentListRequest.offset`](app.schemas.md#app.schemas.document_list.DocumentListRequest.offset)
      * [`DocumentListRequest.order`](app.schemas.md#app.schemas.document_list.DocumentListRequest.order)
      * [`DocumentListRequest.order_by`](app.schemas.md#app.schemas.document_list.DocumentListRequest.order_by)
      * [`DocumentListRequest.updated_date__ge`](app.schemas.md#app.schemas.document_list.DocumentListRequest.updated_date__ge)
      * [`DocumentListRequest.updated_date__le`](app.schemas.md#app.schemas.document_list.DocumentListRequest.updated_date__le)
      * [`DocumentListRequest.user_id__eq`](app.schemas.md#app.schemas.document_list.DocumentListRequest.user_id__eq)
    * [`DocumentListResponse`](app.schemas.md#app.schemas.document_list.DocumentListResponse)
      * [`DocumentListResponse.documents`](app.schemas.md#app.schemas.document_list.DocumentListResponse.documents)
      * [`DocumentListResponse.documents_count`](app.schemas.md#app.schemas.document_list.DocumentListResponse.documents_count)
      * [`DocumentListResponse.model_config`](app.schemas.md#app.schemas.document_list.DocumentListResponse.model_config)
  * [app.schemas.document_select module](app.schemas.md#module-app.schemas.document_select)
    * [`DocumentSelectResponse`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse)
      * [`DocumentSelectResponse.checksum`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.checksum)
      * [`DocumentSelectResponse.collection`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.collection)
      * [`DocumentSelectResponse.created_date`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.created_date)
      * [`DocumentSelectResponse.document_revisions`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.document_revisions)
      * [`DocumentSelectResponse.filename`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.filename)
      * [`DocumentSelectResponse.filesize`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.filesize)
      * [`DocumentSelectResponse.flagged`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.flagged)
      * [`DocumentSelectResponse.id`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.id)
      * [`DocumentSelectResponse.latest_revision_number`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.latest_revision_number)
      * [`DocumentSelectResponse.mimetype`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.mimetype)
      * [`DocumentSelectResponse.model_config`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.model_config)
      * [`DocumentSelectResponse.summary`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.summary)
      * [`DocumentSelectResponse.updated_date`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.updated_date)
      * [`DocumentSelectResponse.user`](app.schemas.md#app.schemas.document_select.DocumentSelectResponse.user)
  * [app.schemas.document_update module](app.schemas.md#module-app.schemas.document_update)
    * [`DocumentUpdateRequest`](app.schemas.md#app.schemas.document_update.DocumentUpdateRequest)
      * [`DocumentUpdateRequest.collection_id`](app.schemas.md#app.schemas.document_update.DocumentUpdateRequest.collection_id)
      * [`DocumentUpdateRequest.filename`](app.schemas.md#app.schemas.document_update.DocumentUpdateRequest.filename)
      * [`DocumentUpdateRequest.model_config`](app.schemas.md#app.schemas.document_update.DocumentUpdateRequest.model_config)
      * [`DocumentUpdateRequest.summary`](app.schemas.md#app.schemas.document_update.DocumentUpdateRequest.summary)
    * [`DocumentUpdateResponse`](app.schemas.md#app.schemas.document_update.DocumentUpdateResponse)
      * [`DocumentUpdateResponse.document_id`](app.schemas.md#app.schemas.document_update.DocumentUpdateResponse.document_id)
      * [`DocumentUpdateResponse.latest_revision_number`](app.schemas.md#app.schemas.document_update.DocumentUpdateResponse.latest_revision_number)
      * [`DocumentUpdateResponse.model_config`](app.schemas.md#app.schemas.document_update.DocumentUpdateResponse.model_config)
  * [app.schemas.document_upload module](app.schemas.md#module-app.schemas.document_upload)
    * [`DocumentUploadResponse`](app.schemas.md#app.schemas.document_upload.DocumentUploadResponse)
      * [`DocumentUploadResponse.document_id`](app.schemas.md#app.schemas.document_upload.DocumentUploadResponse.document_id)
      * [`DocumentUploadResponse.latest_revision_number`](app.schemas.md#app.schemas.document_upload.DocumentUploadResponse.latest_revision_number)
      * [`DocumentUploadResponse.model_config`](app.schemas.md#app.schemas.document_upload.DocumentUploadResponse.model_config)
  * [app.schemas.revision_select module](app.schemas.md#module-app.schemas.revision_select)
    * [`RevisionSelectResponse`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse)
      * [`RevisionSelectResponse.checksum`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse.checksum)
      * [`RevisionSelectResponse.created_date`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse.created_date)
      * [`RevisionSelectResponse.document_id`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse.document_id)
      * [`RevisionSelectResponse.filesize`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse.filesize)
      * [`RevisionSelectResponse.id`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse.id)
      * [`RevisionSelectResponse.model_config`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse.model_config)
      * [`RevisionSelectResponse.revision_number`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse.revision_number)
      * [`RevisionSelectResponse.user`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse.user)
      * [`RevisionSelectResponse.uuid`](app.schemas.md#app.schemas.revision_select.RevisionSelectResponse.uuid)
  * [app.schemas.token_invalidate module](app.schemas.md#module-app.schemas.token_invalidate)
    * [`TokenInvalidateResponse`](app.schemas.md#app.schemas.token_invalidate.TokenInvalidateResponse)
      * [`TokenInvalidateResponse.model_config`](app.schemas.md#app.schemas.token_invalidate.TokenInvalidateResponse.model_config)
      * [`TokenInvalidateResponse.user_id`](app.schemas.md#app.schemas.token_invalidate.TokenInvalidateResponse.user_id)
  * [app.schemas.token_retrieve module](app.schemas.md#module-app.schemas.token_retrieve)
    * [`TokenRetrieveRequest`](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveRequest)
      * [`TokenRetrieveRequest.exp`](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveRequest.exp)
      * [`TokenRetrieveRequest.model_config`](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveRequest.model_config)
      * [`TokenRetrieveRequest.totp`](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveRequest.totp)
      * [`TokenRetrieveRequest.username`](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveRequest.username)
    * [`TokenRetrieveResponse`](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveResponse)
      * [`TokenRetrieveResponse.model_config`](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveResponse.model_config)
      * [`TokenRetrieveResponse.user_id`](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveResponse.user_id)
      * [`TokenRetrieveResponse.user_token`](app.schemas.md#app.schemas.token_retrieve.TokenRetrieveResponse.user_token)
  * [app.schemas.user_delete module](app.schemas.md#module-app.schemas.user_delete)
    * [`UserDeleteResponse`](app.schemas.md#app.schemas.user_delete.UserDeleteResponse)
      * [`UserDeleteResponse.model_config`](app.schemas.md#app.schemas.user_delete.UserDeleteResponse.model_config)
      * [`UserDeleteResponse.user_id`](app.schemas.md#app.schemas.user_delete.UserDeleteResponse.user_id)
  * [app.schemas.user_list module](app.schemas.md#module-app.schemas.user_list)
    * [`UserListRequest`](app.schemas.md#app.schemas.user_list.UserListRequest)
      * [`UserListRequest.active__eq`](app.schemas.md#app.schemas.user_list.UserListRequest.active__eq)
      * [`UserListRequest.created_date__ge`](app.schemas.md#app.schemas.user_list.UserListRequest.created_date__ge)
      * [`UserListRequest.created_date__le`](app.schemas.md#app.schemas.user_list.UserListRequest.created_date__le)
      * [`UserListRequest.first_name__ilike`](app.schemas.md#app.schemas.user_list.UserListRequest.first_name__ilike)
      * [`UserListRequest.full_name__ilike`](app.schemas.md#app.schemas.user_list.UserListRequest.full_name__ilike)
      * [`UserListRequest.last_login_date__ge`](app.schemas.md#app.schemas.user_list.UserListRequest.last_login_date__ge)
      * [`UserListRequest.last_login_date__le`](app.schemas.md#app.schemas.user_list.UserListRequest.last_login_date__le)
      * [`UserListRequest.last_name__ilike`](app.schemas.md#app.schemas.user_list.UserListRequest.last_name__ilike)
      * [`UserListRequest.limit`](app.schemas.md#app.schemas.user_list.UserListRequest.limit)
      * [`UserListRequest.model_config`](app.schemas.md#app.schemas.user_list.UserListRequest.model_config)
      * [`UserListRequest.offset`](app.schemas.md#app.schemas.user_list.UserListRequest.offset)
      * [`UserListRequest.order`](app.schemas.md#app.schemas.user_list.UserListRequest.order)
      * [`UserListRequest.order_by`](app.schemas.md#app.schemas.user_list.UserListRequest.order_by)
      * [`UserListRequest.role__eq`](app.schemas.md#app.schemas.user_list.UserListRequest.role__eq)
      * [`UserListRequest.username__ilike`](app.schemas.md#app.schemas.user_list.UserListRequest.username__ilike)
    * [`UserListResponse`](app.schemas.md#app.schemas.user_list.UserListResponse)
      * [`UserListResponse.model_config`](app.schemas.md#app.schemas.user_list.UserListResponse.model_config)
      * [`UserListResponse.users`](app.schemas.md#app.schemas.user_list.UserListResponse.users)
      * [`UserListResponse.users_count`](app.schemas.md#app.schemas.user_list.UserListResponse.users_count)
  * [app.schemas.user_login module](app.schemas.md#module-app.schemas.user_login)
    * [`UserLoginRequest`](app.schemas.md#app.schemas.user_login.UserLoginRequest)
      * [`UserLoginRequest.model_config`](app.schemas.md#app.schemas.user_login.UserLoginRequest.model_config)
      * [`UserLoginRequest.password`](app.schemas.md#app.schemas.user_login.UserLoginRequest.password)
      * [`UserLoginRequest.username`](app.schemas.md#app.schemas.user_login.UserLoginRequest.username)
    * [`UserLoginResponse`](app.schemas.md#app.schemas.user_login.UserLoginResponse)
      * [`UserLoginResponse.model_config`](app.schemas.md#app.schemas.user_login.UserLoginResponse.model_config)
      * [`UserLoginResponse.password_accepted`](app.schemas.md#app.schemas.user_login.UserLoginResponse.password_accepted)
      * [`UserLoginResponse.user_id`](app.schemas.md#app.schemas.user_login.UserLoginResponse.user_id)
  * [app.schemas.user_password module](app.schemas.md#module-app.schemas.user_password)
    * [`UserPasswordRequest`](app.schemas.md#app.schemas.user_password.UserPasswordRequest)
      * [`UserPasswordRequest.current_password`](app.schemas.md#app.schemas.user_password.UserPasswordRequest.current_password)
      * [`UserPasswordRequest.model_config`](app.schemas.md#app.schemas.user_password.UserPasswordRequest.model_config)
      * [`UserPasswordRequest.updated_password`](app.schemas.md#app.schemas.user_password.UserPasswordRequest.updated_password)
    * [`UserPasswordResponse`](app.schemas.md#app.schemas.user_password.UserPasswordResponse)
      * [`UserPasswordResponse.model_config`](app.schemas.md#app.schemas.user_password.UserPasswordResponse.model_config)
      * [`UserPasswordResponse.user_id`](app.schemas.md#app.schemas.user_password.UserPasswordResponse.user_id)
  * [app.schemas.user_register module](app.schemas.md#module-app.schemas.user_register)
    * [`UserRegisterRequest`](app.schemas.md#app.schemas.user_register.UserRegisterRequest)
      * [`UserRegisterRequest.first_name`](app.schemas.md#app.schemas.user_register.UserRegisterRequest.first_name)
      * [`UserRegisterRequest.last_name`](app.schemas.md#app.schemas.user_register.UserRegisterRequest.last_name)
      * [`UserRegisterRequest.model_config`](app.schemas.md#app.schemas.user_register.UserRegisterRequest.model_config)
      * [`UserRegisterRequest.password`](app.schemas.md#app.schemas.user_register.UserRegisterRequest.password)
      * [`UserRegisterRequest.summary`](app.schemas.md#app.schemas.user_register.UserRegisterRequest.summary)
      * [`UserRegisterRequest.username`](app.schemas.md#app.schemas.user_register.UserRegisterRequest.username)
    * [`UserRegisterResponse`](app.schemas.md#app.schemas.user_register.UserRegisterResponse)
      * [`UserRegisterResponse.mfa_secret`](app.schemas.md#app.schemas.user_register.UserRegisterResponse.mfa_secret)
      * [`UserRegisterResponse.model_config`](app.schemas.md#app.schemas.user_register.UserRegisterResponse.model_config)
      * [`UserRegisterResponse.user_id`](app.schemas.md#app.schemas.user_register.UserRegisterResponse.user_id)
  * [app.schemas.user_role module](app.schemas.md#module-app.schemas.user_role)
    * [`UserRoleRequest`](app.schemas.md#app.schemas.user_role.UserRoleRequest)
      * [`UserRoleRequest.active`](app.schemas.md#app.schemas.user_role.UserRoleRequest.active)
      * [`UserRoleRequest.model_config`](app.schemas.md#app.schemas.user_role.UserRoleRequest.model_config)
      * [`UserRoleRequest.role`](app.schemas.md#app.schemas.user_role.UserRoleRequest.role)
      * [`UserRoleRequest.validate_role()`](app.schemas.md#app.schemas.user_role.UserRoleRequest.validate_role)
    * [`UserRoleResponse`](app.schemas.md#app.schemas.user_role.UserRoleResponse)
      * [`UserRoleResponse.model_config`](app.schemas.md#app.schemas.user_role.UserRoleResponse.model_config)
      * [`UserRoleResponse.user_id`](app.schemas.md#app.schemas.user_role.UserRoleResponse.user_id)
  * [app.schemas.user_select module](app.schemas.md#module-app.schemas.user_select)
    * [`UserSelectResponse`](app.schemas.md#app.schemas.user_select.UserSelectResponse)
      * [`UserSelectResponse.active`](app.schemas.md#app.schemas.user_select.UserSelectResponse.active)
      * [`UserSelectResponse.created_date`](app.schemas.md#app.schemas.user_select.UserSelectResponse.created_date)
      * [`UserSelectResponse.first_name`](app.schemas.md#app.schemas.user_select.UserSelectResponse.first_name)
      * [`UserSelectResponse.has_thumbnail`](app.schemas.md#app.schemas.user_select.UserSelectResponse.has_thumbnail)
      * [`UserSelectResponse.id`](app.schemas.md#app.schemas.user_select.UserSelectResponse.id)
      * [`UserSelectResponse.last_login_date`](app.schemas.md#app.schemas.user_select.UserSelectResponse.last_login_date)
      * [`UserSelectResponse.last_name`](app.schemas.md#app.schemas.user_select.UserSelectResponse.last_name)
      * [`UserSelectResponse.model_config`](app.schemas.md#app.schemas.user_select.UserSelectResponse.model_config)
      * [`UserSelectResponse.role`](app.schemas.md#app.schemas.user_select.UserSelectResponse.role)
      * [`UserSelectResponse.summary`](app.schemas.md#app.schemas.user_select.UserSelectResponse.summary)
      * [`UserSelectResponse.username`](app.schemas.md#app.schemas.user_select.UserSelectResponse.username)
  * [app.schemas.user_update module](app.schemas.md#module-app.schemas.user_update)
    * [`UserUpdateRequest`](app.schemas.md#app.schemas.user_update.UserUpdateRequest)
      * [`UserUpdateRequest.first_name`](app.schemas.md#app.schemas.user_update.UserUpdateRequest.first_name)
      * [`UserUpdateRequest.last_name`](app.schemas.md#app.schemas.user_update.UserUpdateRequest.last_name)
      * [`UserUpdateRequest.model_config`](app.schemas.md#app.schemas.user_update.UserUpdateRequest.model_config)
      * [`UserUpdateRequest.summary`](app.schemas.md#app.schemas.user_update.UserUpdateRequest.summary)
    * [`UserUpdateResponse`](app.schemas.md#app.schemas.user_update.UserUpdateResponse)
      * [`UserUpdateResponse.model_config`](app.schemas.md#app.schemas.user_update.UserUpdateResponse.model_config)
      * [`UserUpdateResponse.user_id`](app.schemas.md#app.schemas.user_update.UserUpdateResponse.user_id)
  * [app.schemas.userpic_delete module](app.schemas.md#module-app.schemas.userpic_delete)
    * [`UserpicDeleteResponse`](app.schemas.md#app.schemas.userpic_delete.UserpicDeleteResponse)
      * [`UserpicDeleteResponse.model_config`](app.schemas.md#app.schemas.userpic_delete.UserpicDeleteResponse.model_config)
      * [`UserpicDeleteResponse.user_id`](app.schemas.md#app.schemas.userpic_delete.UserpicDeleteResponse.user_id)
  * [app.schemas.userpic_upload module](app.schemas.md#module-app.schemas.userpic_upload)
    * [`UserpicUploadResponse`](app.schemas.md#app.schemas.userpic_upload.UserpicUploadResponse)
      * [`UserpicUploadResponse.model_config`](app.schemas.md#app.schemas.userpic_upload.UserpicUploadResponse.model_config)
      * [`UserpicUploadResponse.user_id`](app.schemas.md#app.schemas.userpic_upload.UserpicUploadResponse.user_id)
  * [Module contents](app.schemas.md#module-app.schemas)

## Submodules

## app.app module

Hidden — main application module.

This module assembles the FastAPI application, connects core services,
mounts all routers, and defines global behavior. On startup, it loads
configuration, opens database and cache connections, and places shared
components into the application state. If lockdown mode is enabled, it
is forcibly disabled. On shutdown, all resources are released cleanly.

For every request, assign a UUID, measure and log duration, check the
lockdown state, and validate the secret key. Request logging is enabled
at DEBUG level.

Errors are handled centrally to produce consistent JSON. Returns 422 for
validation; 498/499 for secret-key issues; 423 for lockdown mode; 409
for file conflicts; 401/403 for auth errors. All other exceptions become
500. Every non-validation issue is logged with elapsed time and a stack
trace, and the response includes the request UUID (X-Request-ID). Error
logging is enabled at ERROR level.

### *async* app.app.exception_handler(request: Request, e: Exception)

Handles exceptions and returns consistent JSON errors; logs elapsed
time (with stack trace for server errors) and appends X-Request-ID.

### app.app.lifespan(app: FastAPI)

Initializes core services and a shared file manager on startup. On
shutdown, disposes database resources and closes cache connections.

### *async* app.app.middleware_handler(request: Request, call_next)

Binds a request-scoped logger, logs request timing, checks lockdown
state, reads the secret key, appends X-Request-ID to the response.

## app.auth module

Provides authentication and permission checks based on JWT tokens,
mapping user roles to functions that validate their access rights
and raising detailed errors on invalid or expired tokens.

### app.auth.auth(user_role: [UserRole](app.models.md#app.models.user.UserRole)) → Callable

Returns a FastAPI dependency enforcing permissions for the specified
role by mapping application roles to permission-check functions that
gate access to protected routes.

## app.config module

Defines the application configuration as a dataclass and loads values
from an .env file using the python-dotenv library, converting them
to the appropriate types; uses lru_cache to memoize the resulting
configuration object for efficient reuse.

### *class* app.config.Config(SECRET_KEY_PATH: str, SECRET_KEY_LENGTH: int, SECRET_KEY_WATCHDOG_INTERVAL_SECONDS: int, DATA_MOUNTPOINT: str, DATA_CIPHER_DIR: str, CRYPTO_KEY_LENGTH: int, CRYPTO_NONCE_LENGTH: int, CRYPTO_HKDF_INFO: bytes, CRYPTO_HKDF_SALT_B64: str, CRYPTO_DERIVE_WITH_HKDF: bool, CRYPTO_DEFAULT_ENCODING: str, CRYPTO_AAD_DEFAULT: bytes, LOCK_FILE_PATH: str, LOG_LEVEL: str, LOG_NAME: str, LOG_FORMAT: str, LOG_FILENAME: str, LOG_FILESIZE: int, LOG_FILES_LIMIT: int, UVICORN_HOST: str, UVICORN_PORT: int, UVICORN_WORKERS: int, SQLITE_PATH: str, SQLITE_POOL_SIZE: int, SQLITE_POOL_OVERFLOW: int, SQLITE_SQL_ECHO: bool, REDIS_ENABLED: bool, REDIS_HOST: str, REDIS_PORT: int, REDIS_DECODE_RESPONSES: bool, REDIS_EXPIRE: int, LRU_TOTAL_SIZE_BYTES: int, LRU_ITEM_SIZE_LIMIT_BYTES: int, FILE_CHUNK_SIZE: int, FILE_SHRED_CYCLES: int, FILE_DEFAULT_MIMETYPE: str, JTI_LENGTH: int, JWT_ALGORITHMS: list, JWT_SECRET: str, ADDONS_PATH: str, ADDONS_LIST: list, AUTH_PASSWORD_ATTEMPTS: int, AUTH_TOTP_ATTEMPTS: int, AUTH_SUSPENDED_TIME: int, DOCUMENTS_DIR: str, REVISIONS_DIR: str, TEMPORARY_DIR: str, THUMBNAILS_DIR: str, THUMBNAILS_WIDTH: int, THUMBNAILS_HEIGHT: int, THUMBNAILS_QUALITY: int)

Bases: `object`

Strongly typed configuration where field names must match keys
in the .env file; values are trimmed and converted according to
their annotated types.

#### ADDONS_LIST *: list*

#### ADDONS_PATH *: str*

#### AUTH_PASSWORD_ATTEMPTS *: int*

#### AUTH_SUSPENDED_TIME *: int*

#### AUTH_TOTP_ATTEMPTS *: int*

#### CRYPTO_AAD_DEFAULT *: bytes*

#### CRYPTO_DEFAULT_ENCODING *: str*

#### CRYPTO_DERIVE_WITH_HKDF *: bool*

#### CRYPTO_HKDF_INFO *: bytes*

#### CRYPTO_HKDF_SALT_B64 *: str*

#### CRYPTO_KEY_LENGTH *: int*

#### CRYPTO_NONCE_LENGTH *: int*

#### DATA_CIPHER_DIR *: str*

#### DATA_MOUNTPOINT *: str*

#### DOCUMENTS_DIR *: str*

#### FILE_CHUNK_SIZE *: int*

#### FILE_DEFAULT_MIMETYPE *: str*

#### FILE_SHRED_CYCLES *: int*

#### JTI_LENGTH *: int*

#### JWT_ALGORITHMS *: list*

#### JWT_SECRET *: str*

#### LOCK_FILE_PATH *: str*

#### LOG_FILENAME *: str*

#### LOG_FILESIZE *: int*

#### LOG_FILES_LIMIT *: int*

#### LOG_FORMAT *: str*

#### LOG_LEVEL *: str*

#### LOG_NAME *: str*

#### LRU_ITEM_SIZE_LIMIT_BYTES *: int*

#### LRU_TOTAL_SIZE_BYTES *: int*

#### REDIS_DECODE_RESPONSES *: bool*

#### REDIS_ENABLED *: bool*

#### REDIS_EXPIRE *: int*

#### REDIS_HOST *: str*

#### REDIS_PORT *: int*

#### REVISIONS_DIR *: str*

#### SECRET_KEY_LENGTH *: int*

#### SECRET_KEY_PATH *: str*

#### SECRET_KEY_WATCHDOG_INTERVAL_SECONDS *: int*

#### SQLITE_PATH *: str*

#### SQLITE_POOL_OVERFLOW *: int*

#### SQLITE_POOL_SIZE *: int*

#### SQLITE_SQL_ECHO *: bool*

#### TEMPORARY_DIR *: str*

#### THUMBNAILS_DIR *: str*

#### THUMBNAILS_HEIGHT *: int*

#### THUMBNAILS_QUALITY *: int*

#### THUMBNAILS_WIDTH *: int*

#### UVICORN_HOST *: str*

#### UVICORN_PORT *: int*

#### UVICORN_WORKERS *: int*

### app.config.get_config() → [Config](#app.config.Config)

Loads configuration settings from an .env file and returns them as
a Config dataclass instance. The function uses type annotations to
convert the environment variable values to their appropriate types,
such as bool, int, list, str or bytes.

## app.constants module

## app.error module

Centralized error definitions and HTTPException wrapper ensuring
consistent error codes and unified response format across the API.

### *exception* app.error.E(loc: list, error_input: str, error_type: str, status_code: int)

Bases: `HTTPException`

Unified HTTPException wrapper that produces error details in the
same shape as Pydantic validation errors.

## app.hook module

Provides an application hook system: loads add-on modules listed in the
config, discovers async handlers named after known hooks, and registers
them for post-event execution.

### *class* app.hook.Hook(request: Request, session: AsyncSession, cache: Redis, current_user: [User](app.models.md#app.models.user.User))

Bases: `object`

Executes registered hook handlers from app state, passing the
request session, Redis cache, the current user, and any extra
arguments.

#### *async* call(hook: str, \*args, \*\*kwargs)

Runs all handlers registered for the given hook in order,
passing session, cache, current user, and provided args/kwargs.

### app.hook.init_hooks(app: FastAPI) → None

Builds the hook registry by importing add-on modules from the
configured path and registering async functions whose names match
constants in enabled hooks.

## app.log module

Initializes a global app logger.

### app.log.init_logger(app: FastAPI) → Logger

Creates a logger from config, attaches a rotating handler,
sets level, stores it in app state, and returns it.

## app.lru module

### *class* app.lru.LRU(cache_size_bytes: int, item_size_bytes: int | None = None)

Bases: `object`

LRU cache that stores bytes under string keys.
Limited both by total size in bytes and optional per-item size.

#### clear() → None

Clear cache completely.

#### *property* count *: int*

Number of cached entries.

#### delete(path: str) → None

Remove a key if present.

#### load(path: str) → bytes | None

Return cached value or None if not found.

#### save(path: str, value: bytes) → None

Insert or update a key, enforcing size limits.

#### *property* size *: int*

Total size of all cached entries in bytes.

## app.redis module

Provides an asynchronous Redis client managed via FastAPI lifespan:
the client is created from runtime settings, stored in app.state for
reuse, exposed through a request-scoped dependency, and optionally
initialized on startup.

### *class* app.redis.RedisClient(, host: str, port: int, decode_responses: bool = True)

Bases: `object`

Holds a shared asyncio Redis client built from configuration and
intended to be instantiated during application startup and reused
across requests via app.state.

#### *async* close() → None

Close the underlying connection pool on application shutdown.

### *async* app.redis.get_cache(request: Request) → AsyncGenerator[Redis, None]

Yield the shared Redis client from app.state without closing it per
request so the connection pool can be reused efficiently across the
application.

### *async* app.redis.init_cache(client: [RedisClient](#app.redis.RedisClient)) → None

Optionally initialize the cache by checking connectivity and
performing startup tasks like a database flush if desired.

## app.repository module

Defines a repository class that manages CRUD operations and caching for
SQLAlchemy models using an asynchronous session for database operations
and Redis for cache storage. Provides methods for existence checks,
insertion, selection, updating, deletion, counting, summation, and
transaction management with commit and rollback.

### *class* app.repository.Repository(session: AsyncSession, cache: Redis, entity_class: Type[DeclarativeBase], config: [Config](#app.config.Config))

Bases: `object`

Provides a unified interface for performing CRUD operations on
SQLAlchemy models with integrated Redis caching.

#### *async* commit()

Commits the current transaction for pending changes in the
database.

#### *async* count_all(\*\*kwargs) → int

Counts the number of SQLAlchemy models that match the given
criteria.

#### *async* delete(entity: DeclarativeBase, commit: bool = True)

Deletes an entity from the database and removes its entry from
the cache if caching is enabled.

#### *async* delete_all(commit: bool = False, \*\*kwargs)

Deletes all SQLAlchemy models from the database  and cache that
match the given criteria.

#### *async* delete_all_from_cache()

Deletes all entities of the managed SQLAlchemy model matching
the criteria from the database and clears them from the cache.

#### *async* delete_from_cache(entity: DeclarativeBase)

Deletes an entity of the managed SQLAlchemy model from the cache
without affecting the database.

#### *async* exists(\*\*kwargs) → bool

Checks if a SQLAlchemy model matching the given criteria exists
in the database.

#### *async* insert(entity: DeclarativeBase, commit: bool = True)

Inserts a new entity of the managed SQLAlchemy model into the
database.

#### *async* rollback()

Rolls back the current transaction, discarding pending changes
in case of errors or inconsistencies.

#### *async* select(\*\*kwargs) → DeclarativeBase | None

Retrieves a SQLAlchemy model based on the provided criteria
or its ID.

#### *async* select_all(\*\*kwargs) → List[DeclarativeBase]

Retrieves all SQLAlchemy models from the database that match
the given criteria.

#### *async* sum_all(column_name: str, \*\*kwargs) → int

Calculates the sum of a specific column for all SQLAlchemy
models matching the criteria.

#### *async* update(entity: DeclarativeBase, commit: bool = True)

Updates an existing SQLAlchemy model in the database and
deletes from cache.

## app.rwlock module

Asyncio reader–writer lock with writer preference.

### *class* app.rwlock.RWLock

Bases: `object`

Asyncio-friendly readers-writer lock with writer preference:
multiple readers may proceed concurrently, writers acquire
exclusive access, and new readers are blocked while any writer
is active or waiting. Non-reentrant and in-process only;
cancellation-safe.

#### read()

Acquire a shared read lock: waits while a writer is active or
queued, then yields; releases on exit and wakes waiters when
the last reader leaves.

#### write()

Acquire an exclusive write lock: announces writer intent to
block new readers, waits for current readers to drain, then
yields; releases on exit and wakes pending readers/writers.

## app.sqlite module

Sets up async SQLite engine and sessions for SQLAlchemy. The engine
and session factory are created from a Config instance and should be
constructed in FastAPI lifespan and stored in app.state.

### *class* app.sqlite.Base(\*\*kwargs: Any)

Bases: `DeclarativeBase`

#### metadata *: ClassVar[MetaData]* *= MetaData()*

Refers to the `_schema.MetaData` collection that will be used
for new `_schema.Table` objects.

#### SEE ALSO
orm_declarative_metadata

#### registry *: ClassVar[\_RegistryType]* *= <sqlalchemy.orm.decl_api.registry object>*

Refers to the `_orm.registry` in use where new
`_orm.Mapper` objects will be associated.

### *class* app.sqlite.SessionManager(, sqlite_path: str, sql_echo: bool = False)

Bases: `object`

Creates and manages the SQLite async engine and session factory
derived from runtime settings, intended to be instantiated during
application startup and reused via app.state for handling database
access.

#### *property* connection_string *: str*

Return the SQLAlchemy async URL for aiosqlite that points
at the resolved database file path.

#### *property* db_path *: str*

Return the absolute filesystem path to the database file with
user home expansion and normalization applied.

#### get_session() → AsyncSession

Return a task-scoped AsyncSession so that concurrent coroutines
receive isolated sessions bound to their current asyncio task.

### *async* app.sqlite.get_session(request: Request) → AsyncGenerator[AsyncSession, None]

Yield an AsyncSession obtained from the SessionManager stored in
app.state and wrap it in a simple unit-of-work pattern that commits
on success, rolls back on error, and always closes the session.

### *async* app.sqlite.init_database(session_manager: [SessionManager](#app.sqlite.SessionManager)) → None

Create the database schema for all mapped models by running
create_all against the async engine at application startup.

## app.version module

## Module contents
