# Transaction

A reference to a transaction.

The `Transaction` object passed to a transaction's updateFunction provides the methods to read and write data within the transaction context. See `Firestore.runTransaction()`.

## Methods

### delete
[method]delete(documentRef) returns [ref firestore.Transaction];[/method]

Deletes the document referred to by the provided `DocumentReference`.

| Parameter |         |
| --------- | ------- |
| documentRef  | **[ref firestore.DocumentReference]** <br /> A reference to the document to be deleted. <br /> Value must not be null. |

### get
[method]get(documentRef) returns Promise containing [ref firestore.DocumentSnapshot];[/method]

Reads the document referenced by the provided `DocumentReference`.

| Parameter |         |
| --------- | ------- |
| documentRef  | **[ref firestore.DocumentReference]** <br /> A reference to the document to be retrieved. <br /> Value must not be null. |

### set
[method]set(documentRef, data, options) returns Promise containing [ref firestore.Transaction];[/method]

Writes to the document referred to by the provided `DocumentReference`. If the document does not exist yet, it will be created. If you pass options, the provided data can be merged into the existing document.

| Parameter |         |
| --------- | ------- |
| documentRef  | **[ref firestore.DocumentReference]** <br /> A reference to the document to be created. <br /> Value must not be null. |
| data         | **Object** <br /> An object of the fields and values for the document. <br /> Value must not be null. |
| options      | **[ref firestore.SetOptions]** (optional) <br /> An object to configure the set behavior. Pass **{merge: true}** to only replace the values specified in the data argument. Fields omitted will remain untouched. |

### update
[method]update(documentRef, ...var_args) returns [ref firestore.Transaction];[/method]

Updates fields in the document referred to by this DocumentReference. The update will fail if applied to a document that does not exist.

Nested fields can be updated by providing dot-separated field path strings or by providing FieldPath objects.

| Parameter |         |
| --------- | ------- |
| documentRef  | **[ref firestore.DocumentReference]** <br /> A reference to the document to be created. <br /> Value must not be null. |
| var_args  | **any type** <br /> Either an object containing all of the fields and values to update, or a series of arguments alternating between fields (as string or objects) and values. <br /> Value may be repeated. |
