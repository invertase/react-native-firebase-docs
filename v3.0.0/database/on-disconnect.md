# OnDisconnect

The onDisconnect class allows you to write or clear data when your client disconnects from the Database server. These updates occur whether your client disconnects cleanly or not, so you can rely on them to clean up data even if a connection is dropped or a client crashes.

The onDisconnect class is most commonly used to manage presence in applications where it is useful to detect how many clients are connected and when other clients disconnect.

To avoid problems when a connection is dropped before the requests can be transferred to the Database server, these functions should be called before writing any data.

Note that onDisconnect operations are only triggered once. If you want an operation to occur each time a disconnect occurs, you'll need to re-establish the onDisconnect operations each time you reconnect.

## Methods

### cancel
[method]cancel(onComplete) returns Promise containing void;[/method]

Cancels all previously queued onDisconnect() set or update events for this location and all children.

If a write has been queued for this location via a set() or update() at a parent location, the write at this location will be canceled, though writes to sibling locations will still occur.

| Parameter |         |
| --------- | ------- |
| onComplete   | **function(nullable Error)** (optional) <br /> An optional callback function that will be called when synchronization to the server has completed. The callback will be passed a single parameter: null for success, or an Error object indicating a failure. |

#### Example

```js
const ref = firebase.database().ref("onlineState");
ref.onDisconnect().set(false);
// ... sometime later
ref.onDisconnect().cancel();
```

### remove
[method]remove(onComplete) returns Promise containing void;[/method]

Ensures the data at this location is deleted when the client is disconnected (due to closing the browser, navigating to a new page, or network issues).

| Parameter |         |
| --------- | ------- |
| onComplete   | **function(nullable Error)** (optional) <br /> An optional callback function that will be called when synchronization to the server has completed. The callback will be passed a single parameter: null for success, or an Error object indicating a failure. |

### set
[method]set(value, onComplete) returns Promise containing void;[/method]

Ensures the data at this location is set to the specified value when the client is disconnected (due to closing the browser, navigating to a new page, or network issues).

set() is especially useful for implementing "presence" systems, where a value should be changed or cleared when a user disconnects so that they appear "offline" to other users.

Note that onDisconnect operations are only triggered once. If you want an operation to occur each time a disconnect occurs, you'll need to re-establish the onDisconnect operations each time.

| Parameter |         |
| --------- | ------- |
| value   | **any type** <br /> The value to be written to this location on disconnect (can be an object, array, string, number, boolean, or null). |
| onComplete   | **function(nullable Error)** (optional) <br /> An optional callback function that will be called when synchronization to the server has completed. The callback will be passed a single parameter: null for success, or an Error object indicating a failure. |

### setWithPriority
[method]setWithPriority(value, priority, onComplete) returns Promise containing void;[/method]

Ensures the data at this location is set to the specified value and priority when the client is disconnected (due to closing the browser, navigating to a new page, or network issues).

| Parameter |         |
| --------- | ------- |
| value   | **any type** <br /> The value to be written to this location on disconnect (can be an object, array, string, number, boolean, or null). |
| priority   | **number** or **string** or **null**  |
| onComplete   | **function(nullable Error)** (optional) <br /> An optional callback function that will be called when synchronization to the server has completed. The callback will be passed a single parameter: null for success, or an Error object indicating a failure. |

### update
[method]update(values, onComplete) returns Promise containing void;[/method]

Writes multiple values at this location when the client is disconnected (due to closing the browser, navigating to a new page, or network issues).

The values argument contains multiple property-value pairs that will be written to the Database together. Each child property can either be a simple property (for example, "name") or a relative path (for example, "name/first") from the current location to the data to update.

As opposed to the set() method, update() can be use to selectively update only the referenced properties at the current location (instead of replacing all the child properties at the current location).

See more examples using the connected version of [update()](version /database/ref#update).

| Parameter |         |
| --------- | ------- |
| value   | **Object** <br /> Object containing multiple values. <br /> Value must not be null. |
| onComplete   | **function(nullable Error)** (optional) <br /> An optional callback function that will be called when synchronization to the server has completed. The callback will be passed a single parameter: null for success, or an Error object indicating a failure. |
