# FieldValue

```
firebase.firestore.FieldValue
```

Sentinel values that can be used when writing document fields with set() or update().

## Methods

### delete
[methods]delete() returns [ref firestore.FieldValue];[/methods]

Returns a sentinel for use with update() to mark a field for deletion.

### serverTimestamp
[methods]serverTimestamp() returns [ref firestore.FieldValue];[/methods]

Returns a sentinel used with set() or update() to include a server-generated timestamp in the written data.
