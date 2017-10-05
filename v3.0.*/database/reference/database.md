# Realtime Database		
 		
```		
firebase.database		
```		
 		
### database		
[method]database(app) returns [ref databbase.Database];[/method]		
 		
Gets the [ref databbase.Database] service for the default app or a given app.		
 		
firebase.database() can be called with no arguments to access the default app's Database service or as firebase.database(app) to access the Database service associated with a specific app.		
 		
firebase.database is also a namespace that can be used to access global constants and methods associated with the Database service.		
 		
| Parameter |         |		
| --------- | ------- |		
| app  | **[ref core.FirebaseApp]** (optional) <br /> Optional app whose Database service to return. If not provided, the default Database service will be returned. <br /> Value must not be null. |		
 		
## Interfaces		
 		
### Database		
 		
[ref database.Database]
 		
### DataSnapshot		

[ref database.DataSnapshot]
 		
### OnDisconnect		

[ref database.OnDisconnect]
 		
### Query		
 		
[ref database.Query]
 		
### Reference		
 		
[ref database.Reference]
 		
## Statics		
 		
### ServerValue		
 		
[ref database.ServerValue]
