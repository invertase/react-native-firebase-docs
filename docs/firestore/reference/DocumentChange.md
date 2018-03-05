# DocumentChange

A DocumentChange represents a change to the documents matching a query. It contains the document affected and the type of change that occurred.

## Properties

### doc
[method]doc returns [ref firestore.DocumentReference];[/method]

The document affected by this change.

### newIndex
[method]newIndex returns number;[/method]

The index of the changed document in the result set immediately after this `DocumentChange` (i.e. supposing that all prior `DocumentChange` objects and the current `DocumentChange` object have been applied). Is -1 for 'removed' events.

### oldIndex
[method]oldIndex returns number;[/method]

The index of the changed document in the result set immediately prior to this `DocumentChange` (i.e. supposing that all prior `DocumentChange` objects have been applied). Is -1 for 'added' events.

### type
[method]type returns string;[/method]

The type of change that occurred.

Possible values are 'added', 'modified', or 'removed'.
