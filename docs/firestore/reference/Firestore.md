# Firestore

The Firebase Firestore service interface.

Do not call this constructor directly. Instead, use `firebase.firestore()`.

> Please note that Persistence (offline support) is enabled by default with Firestore on iOS and Android.

## Properties

### app
[method]app return [ref core.FirebaseApp];[/method]

The app associated with this Firestore service instance.

## Methods

### batch
[method]batch() returns [ref firestore.WriteBatch];[/method]

Creates a write batch, used for performing multiple writes as a single atomic operation.

### collection
[method]collection(collectionPath) returns [ref firestore.CollectionReference];[/method]

Gets a slash-separated path to a collection.

| Parameter |         |
| --------- | ------- |
| collectionPath  | **string** <br /> A slash-separated path to a collection. |

### doc
[method]doc(documentPath) returns [ref firestore.DocumentReference];[/method]

Gets a DocumentReference instance that refers to the document at the specified path.

| Parameter |         |
| --------- | ------- |
| documentPath  | **string** <br /> A slash-separated path to a document. |

## Unsupported Methods

### enablePersistence

### runTransaction

### settings
