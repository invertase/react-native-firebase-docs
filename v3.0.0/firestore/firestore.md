# Firestore

The Firebase Firestore service interface.

Do not call this constructor directly. Instead, use `firebase.firestore()`.

## Methods

### batch
[method]batch() returns [WriteBatch](version /firestore/write-batch)[/method]

Creates a write batch, used for performing multiple writes as a single atomic operation.

### collection
[method]collection(collectionPath) returns [CollectionReference](version /firestore/collection-reference)[/method]

Gets a slash-separated path to a collection.

| Parameter |         |
| --------- | ------- |
| collectionPath  | **string** <br /> A slash-separated path to a collection. |

### doc
[method]doc(documentPath) returns [DocumentReference](version /firestore/document-reference)[/method]

Gets a DocumentReference instance that refers to the document at the specified path.

| Parameter |         |
| --------- | ------- |
| documentPath  | **string** <br /> A slash-separated path to a document. |

## Unsupported Methods

### enablePersistence

### runTransaction

### settings
