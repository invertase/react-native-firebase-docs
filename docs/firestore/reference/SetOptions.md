# SetOptions

An options object that configures the behavior of `set()` calls in [ref firestore.DocumentReference], [ref firestore.WriteBatch] and [ref firestore.Transaction]. These calls can be configured to perform granular merges instead of overwriting the target documents in their entirety by providing a SetOptions with merge: true.

## Properties

### merge
[method]merge returns boolean;[/method]

Changes the behavior of a set() call to only replace the values specified in its data argument. Fields omitted from the set() call remain untouched.