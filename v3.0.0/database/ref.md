# Ref

A Ref represents a specific location in your Database and can be used for reading or writing data to that Database location.

You can reference the root or child location in your Database by calling firebase.database().ref() or firebase.database().ref("child/path").

Writing is done with the set() method and reading can be done with the on() method. 

## Properties

### key
[method]key returns string or null;[/method]

The last part of the `Ref`'s path.

For example, "ada" is the key for https://<DATABASE_NAME>.firebaseio.com/users/ada.

The key of a root `Ref` is null.

### parent
[method]parent returns nullable [Ref](version /database/ref);[/method]

The parent location of a `Ref`.

The parent of a root `Ref` is null.

### ref
[method]ref returns [Ref](version /database/ref);[/method]

Returns a `Ref` to the `Query`'s location.

### root
[method]ref returns [Ref](version /database/ref);[/method]

The root `Ref` of the Database.

## Methods

### child
[method]child(path) returns [Ref](version /database/ref);[/method]

Gets a Ref for the location at the specified relative path.

The relative path can either be a simple child name (for example, "ada") or a deeper slash-separated path (for example, "ada/name/first").

| Parameter |         |
| --------- | ------- |
| path   | **string** <br /> A relative path from this location to the desired child location. |

### endAt
[method]endAt(value, key) returns [Query](version /database/query);[/method]

Creates a Query with the specified ending point.

Using startAt(), endAt(), and equalTo() allows you to choose arbitrary starting and ending points for your queries.

The ending point is inclusive, so children with exactly the specified value will be included in the query. The optional key argument can be used to further limit the range of the query. If it is specified, then children that have exactly the specified value must also have a key name less than or equal to the specified key.

| Parameter |         |
| --------- | ------- |
| value   | **string** <br /> The value to end at. The argument type depends on which orderBy*() function was used in this query. Specify a value that matches the orderBy*() type. When used in combination with orderByKey(). |
| key   | **string** (optional) <br /> The child key to end at, among the children with the previously specified priority. This argument is only allowed if ordering by child, value, or priority. |

### equalTo
[method]equalTo(value, key) returns [Query](version /database/query);[/method]

Creates a Query that includes children that match the specified value.

Using startAt(), endAt(), and equalTo() allows us to choose arbitrary starting and ending points for our queries.

The optional key argument can be used to further limit the range of the query. If it is specified, then children that have exactly the specified value must also have exactly the specified key as their key name. This can be used to filter result sets with many matches for the same value.

| Parameter |         |
| --------- | ------- |
| value   | **string** <br /> The value to end at. The argument type depends on which orderBy*() function was used in this query. Specify a value that matches the orderBy*() type. When used in combination with orderByKey(). |
| key   | **string** (optional) <br /> The child key to end at, among the children with the previously specified priority. This argument is only allowed if ordering by child, value, or priority. |

### isEqual
[method]isEqual(query) returns boolean;[/method]

Returns whether or not the current and provided queries represent the same location, have the same query parameters, and are from the same instance of firebase.app.App.

Two Reference objects are equivalent if they represent the same location and are from the same instance of [FirebaseApp](version /core/firebase-app).

Two Query objects are equivalent if they represent the same location, have the same query parameters, and are from the same instance of [FirebaseApp](version /core/firebase-app). Equivalent queries share the same sort order, limits, and starting and ending points.

| Parameter |         |
| --------- | ------- |
| query   | **[Query](version /database/query)**  |

### limitToFirst
[method]limitToFirst(limit) returns [Query](version /database/query);[/method]

Generates a new Query limited to the first specific number of children.

The limitToFirst() method is used to set a maximum number of children to be synced for a given callback. If we set a limit of 100, we will initially only receive up to 100 child_added events. If we have fewer than 100 messages stored in our Database, a child_added event will fire for each message. However, if we have over 100 messages, we will only receive a child_added event for the first 100 ordered messages. As items change, we will receive child_removed events for each item that drops out of the active list so that the total number stays at 100.

| Parameter |         |
| --------- | ------- |
| limit   | **number** <br /> The maximum number of nodes to include in this query. |

### limitToLast
[method]limitToLast(limit) returns [Query](version /database/query);[/method]

Generates a new Query object limited to the last specific number of children.

The limitToLast() method is used to set a maximum number of children to be synced for a given callback. If we set a limit of 100, we will initially only receive up to 100 child_added events. If we have fewer than 100 messages stored in our Database, a child_added event will fire for each message. However, if we have over 100 messages, we will only receive a child_added event for the last 100 ordered messages. As items change, we will receive child_removed events for each item that drops out of the active list so that the total number stays at 100.

| Parameter |         |
| --------- | ------- |
| limit   | **number** <br /> The maximum number of nodes to include in this query. |

### off
[method]off(eventType, callback, context) returns void;[/method]

Detaches a callback previously attached with on().

Detach a callback previously attached with on(). Note that if on() was called multiple times with the same eventType and callback, the callback will be called multiple times for each event, and off() must be called multiple times to remove the callback. Calling off() on a parent listener will not automatically remove listeners registered on child nodes, off() must also be called on any child listeners to remove the callback.

If a callback is not specified, all callbacks for the specified eventType will be removed. Similarly, if no eventType or callback is specified, all callbacks for the Reference will be removed.

| Parameter |         |
| --------- | ------- |
| eventType   | **string** (optional) <br /> One of the following strings: "value", "child_added", "child_changed", "child_removed", or "child_moved." |
| callback   | **function** (optional) <br /> The callback function that was passed to on(). |
| context   | **Object** (optional) <br /> The context that was passed to on(). |

### on

TODO






