# Realtime Database

```
firebase.database
```

### database
[method]database(app) returns [Database](version /database/database)[/method]

Gets the [Database](version /database/database) service for the default app or a given app.

firebase.database() can be called with no arguments to access the default app's Database service or as firebase.database(app) to access the Database service associated with a specific app.

firebase.database is also a namespace that can be used to access global constants and methods associated with the Database service.

| Parameter |         |
| --------- | ------- |
| app  | **[FirebaseApp](version /core/firebase-app)** Optional <br /> Optional app whose Database service to return. If not provided, the default Database service will be returned. <br /> Value must not be null. |

## Interfaces

### Database

[Database](version /database/database)

### DataSnapshot

[DataSnapshot](version /database/data-snapshot)

### OnDisconnect

[OnDisconnect](version /database/on-disconnect)

### Query

[Query](version /database/query)

### Reference

[Reference](version /database/reference)

## Statics

### ServerValue

[ServerValue](version /database/server-value)
