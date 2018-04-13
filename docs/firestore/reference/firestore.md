# Firestore

The Firebase Firestore service interface.

Do not call this constructor directly. Instead, use `firebase.firestore()`.

> Please note that Persistence (offline support) is enabled by default with Firestore on iOS and Android.

## Properties

### app
[method]app return [ref core.App];[/method]

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

### disableNetwork
[method]disableNetwork() returns Promise containing void;[/method]

Disables network usage for this instance. It can be re-enabled via `enableNetwork()`. While the network is disabled, any snapshot listeners or get() calls will return results from cache, and any write operations will be queued until the network is restored.

### doc
[method]doc(documentPath) returns [ref firestore.DocumentReference];[/method]

Gets a DocumentReference instance that refers to the document at the specified path.

| Parameter |         |
| --------- | ------- |
| documentPath  | **string** <br /> A slash-separated path to a document. |

### enableNetwork
[method]enableNetwork() returns Promise containing void;[/method]

Re-enables use of the network for this Firestore instance after a prior call to `disableNetwork()`.

### runTransaction
[method]runTransaction(updateFunction) returns Promise;[/method]

Executes the given updateFunction and then attempts to commit the changes applied within the transaction. If any document read within the transaction has changed, Cloud Firestore retries the updateFunction. If it fails to commit after 5 attempts, the transaction fails.

> For more information on transactions and examples see our [transactions section](version /firestore/transactions) of the docs.

| Parameter |         |
| --------- | ------- |
| updateFunction | **function**(non-null [ref firestore.Transaction]) <br /> The function to execute within the transaction context. |

## Static Methods

### setLogLevel
[method]setLogLevel(logLevel) returns void;[/method]

Sets the verbosity of Cloud Firestore logs (debug, error, or silent).

| Parameter |         |
| --------- | ------- |
| logLevel  | **string** <br /> The verbosity you set for activity and error logging. Can be any of the following values: <br /> - **debug** for the most verbose logging level, primarily for debugging.<br /> - **error** to log errors only.<br /> - **silent** to turn off logging.|

[collapse Example]
```js
firebase.firestore.setLogLevel('debug');
```
[/collapse]

## Unsupported Methods

### enablePersistence

### enableNetwork

### disableNetwork

### settings
