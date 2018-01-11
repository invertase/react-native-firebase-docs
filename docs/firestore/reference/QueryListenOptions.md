# QueryListenOptions

Options for use with `Query.onSnapshot()` to control the behavior of the snapshot listener.

## Properties

### includeDocumentMetadataChanges
[method]includeDocumentMetadataChanges returns boolean;[/method]

Raise an event even if only metadata of a document in the query results changes (for example, one of the `DocumentSnapshot.metadata` properties on one of the documents). Default is false.

### includeQueryMetadataChanges
[method]includeQueryMetadataChanges returns boolean;[/method]

Raise an event even if only metadata changes (for example, one of the `QuerySnapshot.metadata` properties). Default is false.