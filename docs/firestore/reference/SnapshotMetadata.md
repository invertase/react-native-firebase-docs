# SnapshotMetadata

Metadata about a snapshot, describing the state of the snapshot.

## Properties

### fromCache
[method]fromCache returns boolean;[/method]

True if the snapshot was created from cached data rather than guaranteed up-to-date server data. If your listener has opted into metadata updates (via [ref firestore.MetadataChanges]) you will receive another snapshot with `fromCache` set to false once the client has received up-to-date data from the backend.

### hasPendingWrites
[method]hasPendingWrites returns boolean;[/method]

True if the snapshot includes local writes (`set()` or `update()` calls) that haven't been committed to the backend yet.

If your listener has opted into metadata updates via [ref firestore.MetadataChanges], you receive another snapshot with `hasPendingWrites` set to false once the writes have been committed to the backend.