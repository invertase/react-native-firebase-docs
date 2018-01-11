# DocumentListenOptions

Options for use with `DocumentReference.onSnapshot()` to control the behavior of the snapshot listener.

## Properties

### includeMetadataChanges
[method]includeMetadataChanges returns boolean;[/method]

Raise an event even if only metadata of the document changes (for example, one of the `DocumentSnapshot.metadata` properties on one of the documents). Default is false.
