# WriteBatch

A write batch, used to perform multiple writes as a single atomic unit.

A WriteBatch object can be acquired by calling the Firestore.batch() function. It provides methods for adding writes to the write batch. None of the writes are committed (or visible locally) until WriteBatch.commit() is called.

Unlike transactions, write batches are persisted offline and therefore are preferable when you don't need to condition your writes on read data.

## Methods

### commit
[method]commit() returns Promise containing void;[/method]

Commits all of the writes in this write batch as a single atomic unit.

Returns a promise that resolves once all of the writes in the batch have been successfully written to the backend as an atomic unit. Note that it won't resolve while you're offline.

### delete
[method]delete(documentRef) returns [WriteBatch](version /firestore/write-batch);[/method]

Deletes the document referred to by the provided DocumentReference.

| Parameter |         |
| --------- | ------- |
| documentRef  | **[DocumentReference](version /firestore/document-reference)** <br /> A reference to the document to be deleted. <br /> Value must not be null. |

### set
[method]set(documentRef, data, options) returns [WriteBatch](version /firestore/write-batch);[/method]

Writes to the document referred to by the provided DocumentReference. If the document does not exist yet, it will be created. If you pass options, the provided data can be merged into the existing document.

Returns this WriteBatch instance. Used for chaining method calls.

| Parameter |         |
| --------- | ------- |
| documentRef  | **[DocumentReference](version /firestore/document-reference)** <br /> A reference to the document to be created. <br /> Value must not be null. |
| data  | **Object** <br /> An object of the fields and values for the document. <br /> Value must not be null. |
| options  | **Object** (optional) <br /> An object to configure the set behavior. Pass `{merge: true}` to only replace the values specified in the data argument. Fields omitted will remain untouched. <br /> Value must not be null. |

### update
[method]update(documentRef, ...var_args) returns [WriteBatch](version /firestore/write-batch);[/method]

Updates fields in the document referred to by this DocumentReference. The update will fail if applied to a document that does not exist.

Nested fields can be updated by providing dot-separated field path strings or by providing FieldPath objects.

| Parameter |         |
| --------- | ------- |
| documentRef  | **[DocumentReference](version /firestore/document-reference)** <br /> A reference to the document to be created. <br /> Value must not be null. |
| var_args  | **any type** <br /> Either an object containing all of the fields and values to update, or a series of arguments alternating between fields (as string or objects) and values. <br /> Value may be repeated. |
