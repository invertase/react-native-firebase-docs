# QuerySnapshot

A QuerySnapshot contains zero or more DocumentSnapshot objects representing the results of a query. The documents can be accessed as an array via the docs property or enumerated using the forEach method. The number of documents can be determined via the empty and size properties.

## Properties

### docChanges
[method]docChanges returns Array of [ref firestore.DocumentChange];[/method]

An array of the documents that changed since the last snapshot. If this is the first snapshot, all documents will be in the list as added changes.

### docs
[method]docs returns Array of [ref firestore.DocumentChange];[/method]

An array of all the documents in the QuerySnapshot.

### empty
[method]empty returns boolean;[/method]

True if there are no documents in the QuerySnapshot.

### query
[method]query returns [ref firestore.Query];[/method]

The query you called get or onSnapshot on to get the QuerySnapshot.

### size
[method]size returns number;[/method]

The number of documents in the QuerySnapshot.

## Methods

### forEach
[method]forEach(callback) returns void;[/method]

Enumerates all of the documents in the QuerySnapshot.

| Parameter |         |
| --------- | ------- |
| callback  | **function([ref firestore.DataSnapshot])** |
