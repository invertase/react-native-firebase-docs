# Reference

A Ref represents a specific location in your Database and can be used for reading or writing data to that Database location.

You can reference the root or child location in your Database by calling firebase.database().ref() or firebase.database().ref("child/path").

Writing is done with the set() method and reading can be done with the on() method. 

> The web SDK includes a `Reference` & `ThenableReference` interface. In RNFirebase, `Ref` combines these into one.

## Properties

### key
[method]key returns string or null;[/method]

The last part of the `Reference`'s path.

For example, "ada" is the key for https://<DATABASE_NAME>.firebaseio.com/users/ada.

The key of a root `Reference` is null.

### parent
[method]parent returns nullable [ref database.Reference];[/method]

The parent location of a `Reference`.

The parent of a root `Reference` is null.

### ref
[method]ref returns [ref database.Reference];[/method]

Returns a `Reference` to the `Query`'s location.

### root
[method]root returns [ref database.Reference];[/method]

The root `Reference` of the Database.

## Methods

### child
[method]child(path) returns [ref database.Reference];[/method]

Gets a Ref for the location at the specified relative path.

The relative path can either be a simple child name (for example, "ada") or a deeper slash-separated path (for example, "ada/name/first").

| Parameter |         |
| --------- | ------- |
| path   | **string** <br /> A relative path from this location to the desired child location. |

### endAt
[method]endAt(value, key) returns [ref database.Query];[/method]

Creates a Query with the specified ending point.

Using `startAt()`, `endAt()`, and `equalTo()` allows you to choose arbitrary starting and ending points for your queries.

The ending point is inclusive, so children with exactly the specified value will be included in the query. The optional key argument can be used to further limit the range of the query. If it is specified, then children that have exactly the specified value must also have a key name less than or equal to the specified key.

| Parameter |         |
| --------- | ------- |
| value   | **string** <br /> The value to end at. The argument type depends on which orderBy*() function was used in this query. Specify a value that matches the orderBy*() type. When used in combination with orderByKey(). |
| key   | **string** (optional) <br /> The child key to end at, among the children with the previously specified priority. This argument is only allowed if ordering by child, value, or priority. |

### equalTo
[method]equalTo(value, key) returns [ref database.Query];[/method]

Creates a Query that includes children that match the specified value.

Using `startAt()`, `endAt()`, and `equalTo()` allows us to choose arbitrary starting and ending points for our queries.

The optional key argument can be used to further limit the range of the query. If it is specified, then children that have exactly the specified value must also have exactly the specified key as their key name. This can be used to filter result sets with many matches for the same value.

| Parameter |         |
| --------- | ------- |
| value   | **string** <br /> The value to end at. The argument type depends on which orderBy*() function was used in this query. Specify a value that matches the orderBy*() type. When used in combination with orderByKey(). |
| key   | **string** (optional) <br /> The child key to end at, among the children with the previously specified priority. This argument is only allowed if ordering by child, value, or priority. |

### isEqual
[method]isEqual(query) returns boolean;[/method]

Returns whether or not the current and provided queries represent the same location, have the same query parameters, and are from the same instance of firebase.app.App.

Two Reference objects are equivalent if they represent the same location and are from the same instance of [ref core.FirebaseApp].

Two Query objects are equivalent if they represent the same location, have the same query parameters, and are from the same instance of [ref core.FirebaseApp]. Equivalent queries share the same sort order, limits, and starting and ending points.

| Parameter |         |
| --------- | ------- |
| query   | **[ref database.Query]**  |

### limitToFirst
[method]limitToFirst(limit) returns [ref database.Query];[/method]

Generates a new Query limited to the first specific number of children.

The `limitToFirst()` method is used to set a maximum number of children to be synced for a given callback. If we set a limit of 100, we will initially only receive up to 100 child_added events. If we have fewer than 100 messages stored in our Database, a child_added event will fire for each message. However, if we have over 100 messages, we will only receive a child_added event for the first 100 ordered messages. As items change, we will receive child_removed events for each item that drops out of the active list so that the total number stays at 100.

| Parameter |         |
| --------- | ------- |
| limit   | **number** <br /> The maximum number of nodes to include in this query. |

### limitToLast
[method]limitToLast(limit) returns [ref database.Query];[/method]

Generates a new Query object limited to the last specific number of children.

The `limitToLast()` method is used to set a maximum number of children to be synced for a given callback. If we set a limit of 100, we will initially only receive up to 100 child_added events. If we have fewer than 100 messages stored in our Database, a child_added event will fire for each message. However, if we have over 100 messages, we will only receive a child_added event for the last 100 ordered messages. As items change, we will receive child_removed events for each item that drops out of the active list so that the total number stays at 100.

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
[method]on(eventType, callback, cancelCallbackOrContext, context) returns function();[/method]

Listens for data changes at a particular location.

This is the primary way to read data from a Database. Your callback will be triggered for the initial data and again whenever the data changes. Use off() to stop receiving updates.

The provided callback function is returned unmodified. This is just for convenience if you want to pass an inline function to on() but store the callback function for later passing to off().

#### 'value' event

This event will trigger once with the initial data stored at this location, and then trigger again each time the data changes. The DataSnapshot passed to the callback will be for the location at which on() was called. It won't trigger until the entire contents has been synchronized. If the location has no data, it will be triggered with an empty DataSnapshot (val() will return null).

#### 'child_added' event

This event will be triggered once for each initial child at this location, and it will be triggered again every time a new child is added. The DataSnapshot passed into the callback will reflect the data for the relevant child. For ordering purposes, it is passed a second argument which is a string containing the key of the previous sibling child by sort order, or null if it is the first child.

#### 'child_removed' event

This event will be triggered once every time a child is removed. The DataSnapshot passed into the callback will be the old data for the child that was removed. A child will get removed when either:

- a client explicitly calls remove() on that child or one of its ancestors
- a client calls set(null) on that child or one of its ancestors
- that child has all of its children removed
- there is a query in effect which now filters out the child (because it's sort order changed or the max limit was hit)

#### 'child_changed' event

This event will be triggered when the data stored in a child (or any of its descendants) changes. Note that a single child_changed event may represent multiple changes to the child. The DataSnapshot passed to the callback will contain the new child contents. For ordering purposes, the callback is also passed a second argument which is a string containing the key of the previous sibling child by sort order, or null if it is the first child.

#### 'child_moved' event

This event will be triggered when a child's sort order changes such that its position relative to its siblings changes. The DataSnapshot passed to the callback will be for the data of the child that has moved. It is also passed a second argument which is a string containing the key of the previous sibling child by sort order, or null if it is the first child.

| Parameter |         |
| --------- | ------- |
| eventType   | **string** (optional) <br /> One of the following strings: "value", "child_added", "child_changed", "child_removed", or "child_moved." |
| callback   | **function** <br /> A callback that fires when the specified event occurs. The callback will be passed a DataSnapshot. For ordering purposes, "child_added", "child_changed", and "child_moved" will also be passed a string containing the key of the previous child, by sort order, or null if it is the first child. |
| cancelCallbackOrContext   | **Object** <br /> An optional callback that will be notified if your event subscription is ever canceled because your client does not have permission to read this data (or it had permission but has now lost it). This callback will be passed an Error object indicating why the failure occurred. |
| context   | **Object** (optional) <br /> If provided, this object will be used as this when calling your callback(s). |

### once
[method]once(eventType, successCallback, failureCallbackOrContext, context) returns Promise containing any type;[/method]

Listens for exactly one event of the specified event type, and then stops listening.

This is equivalent to calling on(), and then calling off() inside the callback function. See on() for details on the event types.

| Parameter |         |
| --------- | ------- |
| eventType   | **string** (optional) <br /> One of the following strings: "value", "child_added", "child_changed", "child_removed", or "child_moved." |
| successCallback   | **function** <br /> A callback that fires when the specified event occurs. The callback will be passed a DataSnapshot. For ordering purposes, "child_added", "child_changed", and "child_moved" will also be passed a string containing the key of the previous child, by sort order, or null if it is the first child. |
| cancelCallbackOrContext   | **Object** <br /> An optional callback that will be notified if your event subscription is ever canceled because your client does not have permission to read this data (or it had permission but has now lost it). This callback will be passed an Error object indicating why the failure occurred. |
| context   | **Object** (optional) <br /> If provided, this object will be used as this when calling your callback(s). |

### onDisconnect
[method]onDisconnect() returns [ref database.OnDisconnect];[/method]

### orderByChild
[method]orderByChild(path) returns [ref database.Query];[/method]

Generates a new Query object ordered by the specified child key.

Queries can only order by one key at a time. Calling `orderByChild()` multiple times on the same query is an error.

Firebase queries allow you to order your data by any child key on the fly. However, if you know in advance what your indexes will be, you can define them via the .indexOn rule in your Security Rules for better performance. See the [.indexOn](https://firebase.google.com/docs/database/security/indexing-data) rule for more information.

| Parameter |         |
| --------- | ------- |
| path   | **string** (optional) |

### orderByKey
[method]orderByKey() returns [ref database.Query];[/method]

Generates a new Query object ordered by key.

Sorts the results of a query by their (ascending) key values.

You can read more about orderByKey() in [Sort data](https://firebase.google.com/docs/database/web/lists-of-data#sort_data).

### orderByPriority
[method]orderByPriority() returns [ref database.Query];[/method]

Generates a new Query object ordered by priority.

Applications need not use priority but can order collections by ordinary properties (see [Sort data](https://firebase.google.com/docs/database/web/lists-of-data#sort_data) for alternatives to priority).

### orderByValue
[method]orderByValue() returns [ref database.Query];[/method]

Generates a new Query object ordered by value.

If the children of a query are all scalar values (string, number, or boolean), you can order the results by their (ascending) values.

You can read more about orderByValue() in [Sort data](https://firebase.google.com/docs/database/web/lists-of-data#sort_data).

### push
[method]push(value, onComplete) returns [ref database.Reference];[/method]

Generates a new child location using a unique key and returns its Reference.

This is the most common pattern for adding data to a collection of items.

If you provide a value to push(), the value will be written to the generated location. If you don't pass a value, nothing will be written to the Database and the child will remain empty (but you can use the Reference elsewhere).

The unique key generated by push() are ordered by the current time, so the resulting list of items will be chronologically sorted. The keys are also designed to be unguessable (they contain 72 random bits of entropy).

| Parameter |         |
| --------- | ------- |
| value   | **any type** (optional) <br /> Optional value to be written at the generated location. |
| onComplete   | **function(nullable Error)** (optional) <br /> Callback called when write to server is complete. |

### remove 
[method]remove(onComplete) returns Promise containing void;[/method]

Removes the data at this Database location.

Any data at child locations will also be deleted.

The effect of the remove will be visible immediately and the corresponding event 'value' will be triggered. Synchronization of the remove to the Firebase servers will also be started, and the returned Promise will resolve when complete. If provided, the onComplete callback will be called asynchronously after synchronization has finished.

| Parameter |         |
| --------- | ------- |
| onComplete   | **function(nullable Error)** (optional) <br /> Callback called when write to server is complete. |

### set
[method]set(value, onComplete) returns Promise containing void;[/method]

Writes data to this Database location.

This will overwrite any data at this location and all child locations.

The effect of the write will be visible immediately, and the corresponding events ("value", "child_added", etc.) will be triggered. Synchronization of the data to the Firebase servers will also be started, and the returned Promise will resolve when complete. If provided, the onComplete callback will be called asynchronously after synchronization has finished.

Passing null for the new value is equivalent to calling remove(); namely, all data at this location and all child locations will be deleted.

set() will remove any priority stored at this location, so if priority is meant to be preserved, you need to use setWithPriority() instead.

Note that modifying data with set() will cancel any pending transactions at that location, so extreme care should be taken if mixing set() and transaction() to modify the same data.

A single set() will generate a single "value" event at the location where the set() was performed.

| Parameter |         |
| --------- | ------- |
| value   | **any type** <br /> The value to be written (string, number, boolean, object, array, or null). |
| onComplete   | **function(nullable Error)** (optional) <br /> Callback called when write to server is complete. |

### setPriority
[method]setPriority(priority, onComplete) returns Promise containing void;[/method]

Sets a priority for the data at this Database location.

Applications need not use priority but can order collections by ordinary properties (see [Sorting and filtering data](https://firebase.google.com/docs/database/web/lists-of-data#sorting_and_filtering_data)).

| Parameter |         |
| --------- | ------- |
| priority   | **string** or **number** or **null** |
| onComplete   | **function(nullable Error)** |

### setWithPriority
[method]setPriority(newVal, newPriority, onComplete) returns Promise containing void;[/method]

Writes data the Database location. Like set() but also specifies the priority for that data.

Applications need not use priority but can order collections by ordinary properties (see [Sorting and filtering data](https://firebase.google.com/docs/database/web/lists-of-data#sorting_and_filtering_data)).

| Parameter |         |
| --------- | ------- |
| newVal   | **any type** |
| newPriority   | **string** or **number** or **null** |
| onComplete   | **function(nullable Error)** (optional) |

### startAt
[method]startAt(value, key) returns [ref database.Query];[/method]

Creates a Query with the specified starting point.

Using `startAt()`, `endAt()`, and `equalTo()` allows you to choose arbitrary starting and ending points for your queries.

The starting point is inclusive, so children with exactly the specified value will be included in the query. The optional key argument can be used to further limit the range of the query. If it is specified, then children that have exactly the specified value must also have a key name greater than or equal to the specified key.

You can read more about startAt() in [Filtering data](https://firebase.google.com/docs/database/web/lists-of-data#filtering_data).

| Parameter |         |
| --------- | ------- |
| value   | **string** <br /> The value to start at. The argument type depends on which orderBy*() function was used in this query. Specify a value that matches the orderBy*() type. When used in combination with orderByKey(). |
| key   | **string** <br /> The child key to start at. This argument is only allowed if ordering by child, value, or priority. |

### toJSON
[method]toJSON() returns Object;[/method]

Returns a JSON-serializable representation of this object.

### toString
[method]toString() returns Object;[/method]

Gets the absolute URL for this location.

The toString() method returns a URL that is ready to be put into a browser, curl command, or a firebase.database().refFromURL() call. Since all of those expect the URL to be url-encoded, toString() returns an encoded URL.

Append '.json' to the returned URL when typed into a browser to download JSON-formatted data. If the location is secured (that is, not publicly readable), you will get a permission-denied error.

### transaction
[method]transaction(transactionUpdate, onComplete, applyLocally) returns Promise containing `{committed: boolean, snapshot: nullable DataSnapshot}`;[/method]

Atomically modifies the data at this location.

Atomically modify the data at this location. Unlike a normal set(), which just overwrites the data regardless of its previous value, transaction() is used to modify the existing value to a new value, ensuring there are no conflicts with other clients writing to the same location at the same time.

To accomplish this, you pass transaction() an update function which is used to transform the current value into a new value. If another client writes to the location before your new value is successfully written, your update function will be called again with the new current value, and the write will be retried. This will happen repeatedly until your write succeeds without conflict or you abort the transaction by not returning a value from your update function.

Note: Modifying data with set() will cancel any pending transactions at that location, so extreme care should be taken if mixing set() and transaction() to update the same data.

Note: When using transactions with Security and Firebase Rules in place, be aware that a client needs .read access in addition to .write access in order to perform a transaction. This is because the client-side nature of transactions requires the client to read the data in order to transactionally update it.

| Parameter |         |
| --------- | ------- |
| transactionUpdate   | **function(any type)** <br /> A developer-supplied function which will be passed the current data stored at this location (as a JavaScript object). The function should return the new value it would like written (as a JavaScript object). If `undefined` is returned (i.e. you return with no arguments) the transaction will be aborted and the data at this location will not be modified. |
| onComplete   | **function(nullable Error, boolean, nullable [ref database.DataSnapshot])** (optional) <br /> A callback function that will be called when the transaction completes. The callback is passed three arguments: a possibly-null Error, a boolean indicating whether the transaction was committed, and a DataSnapshot indicating the final result. If the transaction failed abnormally, the first argument will be an Error object indicating the failure cause. If the transaction finished normally, but no data was committed because no data was returned from transactionUpdate, then second argument will be false. If the transaction completed and committed data to Firebase, the second argument will be true. Regardless, the third argument will be a DataSnapshot containing the resulting data in this location. |
| applyLocally   | **boolean** (optional) <br /> By default, events are raised each time the transaction update function runs. So if it is run multiple times, you may see intermediate states. You can set this to false to suppress these intermediate states and instead wait until the transaction has completed before events are raised. |

### update
[method]update(values, onComplete) returns Promise returning void;[/method]

Writes multiple values to the Database at once.

The values argument contains multiple property-value pairs that will be written to the Database together. Each child property can either be a simple property (for example, "name") or a relative path (for example, "name/first") from the current location to the data to update.

As opposed to the set() method, update() can be use to selectively update only the referenced properties at the current location (instead of replacing all the child properties at the current location).

The effect of the write will be visible immediately, and the corresponding events ('value', 'child_added', etc.) will be triggered. Synchronization of the data to the Firebase servers will also be started, and the returned Promise will resolve when complete. If provided, the onComplete callback will be called asynchronously after synchronization has finished.

A single update() will generate a single "value" event at the location where the update() was performed, regardless of how many children were modified.

Note that modifying data with update() will cancel any pending transactions at that location, so extreme care should be taken if mixing update() and transaction() to modify the same data.

Passing null to update() will remove the data at this location.

| Parameter |         |
| --------- | ------- |
| values   | **Object** <br /> TObject containing multiple values. <br /> Value must not be null. |
| onComplete   | **function** (optional) <br /> Callback called when write to server is complete. |
