# Firestore

```
firebase.firestore
```

### firestore
[method]firestore(app) returns [ref firestore.Firestore];[/method]

Gets the [ref firestore.Firestore] service for the default app or a given app.

firebase.firestore() can be called with no arguments to access the default app's Firestore service or as firebase.firestore(app) to access the Firestore service associated with a specific app.

| Parameter |         |
| --------- | ------- |
| app  | **[ref core.FirebaseApp]** (optional) <br /> Optional app whose Firestore service to return. If not provided, the default Firestore service will be returned. <br /> Value must not be null. |

## Interfaces

### CollectionReference

[ref firestore.CollectionReference]

### DocumentReference

[ref firestore.DocumentReference]

### DocumentSnapshot

[ref firestore.DocumentSnapshot]

### DocumentChange

[ref firestore.DocumentChange]

### Firestore

[ref firestore.Firestore]

### GeoPoint

[ref firestore.GeoPoint]

### Query

[ref firestore.Query]

### QuerySnapshot

[ref firestore.QuerySnapshot]

### WriteBatch

[ref firestore.WriteBatch]

## Statics

### FieldValue

[ref firestore.FieldValue]
