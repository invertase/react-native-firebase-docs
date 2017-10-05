# Firestore

```
firebase.firestore
```

### firestore
[method]firestore(app) returns [Firestore](version /firestore/firestore)[/method]

Gets the [Firestore](version /firestore/firestore) service for the default app or a given app.

firebase.firestore() can be called with no arguments to access the default app's Firestore service or as firebase.firestore(app) to access the Firestore service associated with a specific app.

| Parameter |         |
| --------- | ------- |
| app  | **[FirebaseApp](version /core/firebase-app)** (optional) <br /> Optional app whose Firestore service to return. If not provided, the default Firestore service will be returned. <br /> Value must not be null. |

## Interfaces

### CollectionReference

[WriteBatch](version /firestore/collection-reference)

### CollectionReference

[CollectionReference](version /firestore/collection-reference)

### DocumentReference

[DocumentReference](version /firestore/document-reference)

### DocumentSnapshot

[DocumentSnapshot](version /firestore/document-snapshot)

### DocumentChange

[DocumentChange](version /firestore/document-change)

### Firestore

[Firestore](version /firestore/firestore)

### GeoPoint

[GeoPoint](version /firestore/geopoint)

### Query

[Path](version /firestore/query)

### QuerySnapshot

[Path](version /firestore/QuerySnapshot)

### WriteBatch

[WriteBatch](version /firestore/write-batch)

## Statics

### FieldValue

[FieldValue](version /firestore/field-value)
