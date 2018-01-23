# Storage

The Firebase Storage service interface.

```
firebase.storage
```

## Properties

The following properties are accessed via `firebase.storage()`.

### app
[method]app returns [ref core.App];[/method]

The app associated with the Storage service instance.

### maxOperationRetryTime
[method]maxOperationRetryTime returns Number;[/method]

Currently **NOT yet implemented**.

The maximum time to retry operations other than uploads or downloads in milliseconds.

### maxUploadRetryTime
[method]maxUploadRetryTime returns Number;[/method]

Currently **NOT yet implemented**.

The maximum time to retry uploads in milliseconds.


[collapse Example]
```js
const { app } = firebase.storage();
console.log(app.name);
```
[/collapse]

## Methods

The following methods are accessed via `firebase.storage()`.

[collapse Examples]
```js
// get the Storage service for the default app
const defaultStorage = firebase.storage();

// Get the Storage service for a given app
const otherApp = firebase.app('otherAppName');
const otherStorage = firebase.storage(otherApp);
```
[/collapse]

### ref
[method]ref(path) returns [ref storage.Reference];[/method]

Returns a reference for the given path in the default bucket.

| Parameter |         |
| --------- | ------- |
| path  | **string**  |

Path must be a relative path to initialize the reference with, for example path/to/image.jpg. If not passed, the returned reference points to the bucket root.

[collapse Example]
```js
const ref = firebase.storage().ref('path/to/image.jpg');
```
[/collapse]

### refFromURL
[method]refFromURL(url) returns [ref storage.Reference];[/method]

Returns a reference for the given absolute URL.

| Parameter |         |
| --------- | ------- |
| url  | **string**  |


URL must be in the form of either:

   - a gs:// URL, for example gs://bucket/files/image.png
   - a download URL taken from object metadata.

[collapse Example]
```js
const ref = firebase.storage().refFromURL('gs://bucket/path/to/image.jpg');
```
[/collapse]

### setMaxOperationRetryTime
[method]setMaxOperationRetryTime(time) returns void;[/method]

Set a new maximum operation retry time in milliseconds.

| Parameter |         |
| --------- | ------- |
| time  | **number**  |

[collapse Example]
```js
const thirtySecs = 30 * 1000;
firebase.storage().setMaxOperationRetryTime(thirtySecs);
```
[/collapse]

### setMaxUploadRetryTime
[method]setMaxUploadRetryTime(time) returns void;[/method]

Set a new maximum upload retry time in milliseconds.

| Parameter |         |
| --------- | ------- |
| time  | **number**  |

[collapse Example]
```js
const thirtySecs = 30 * 1000;
firebase.storage().setMaxUploadRetryTime(thirtySecs);
```
[/collapse]

## Statics

The following static properties are accessed via `firebase.storage`.

### TaskEvent

**Type**: Object

An event that is triggered on a task.

| Property |
| --------- |
| STATE_CHANGED  |

[collapse Example]
```js
firebase.storage.TaskEvent.STATE_CHANGED;
```
[/collapse]


### TaskState

**Type**: Object

Represents the current state of a running upload.

| Property | Description |
| --------- | ------- |
| RUNNING  | Indicates that the task is still running and making progress. |
| PAUSED   | Indicates that the task is paused |
| SUCCESS  | Indicates that the task completed successfully. |
| CANCELED | Indicates that the task was canceled. |
| ERROR    | Indicates that the task failed for a reason other than being canceled. |

[collapse Examples]
```js
firebase.storage.TaskState.RUNNING;
firebase.storage.TaskState.SUCCESS;
```
[/collapse]

### Native

**Type**: Object

React Native Firebase addition. This object provides full paths to common file paths on the native device, for use with `.putFile()`

| Property | Description |
| --------- | ------- |
| DOCUMENT_DIRECTORY_PATH  |    |
| EXTERNAL_DIRECTORY_PATH  |    |
| EXTERNAL_STORAGE_DIRECTORY_PATH  |    |
| PICTURES_DIRECTORY_PATH  |    |
| EXTERNAL_STORAGE_DIRECTORY_PATH  |    |
| TEMPORARY_DIRECTORY_PATH  |  Path to the devices temp directory.  |
| CACHES_DIRECTORY_PATH  |  Path to the devices cache directory  |
| FILETYPE_REGULAR  |    |
| FILETYPE_DIRECTORY  |    |


[collapse Examples]
```js
firebase.storage.Native.TEMPORARY_DIRECTORY_PATH;
firebase.storage.Native.CACHES_DIRECTORY_PATH;
```
[/collapse]

