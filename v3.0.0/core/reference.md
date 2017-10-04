# Core

## Methods

### initializeApp
[method]initializeApp(options, name) returns [FirebaseApp](version /core/firebase-app);[/method]

Initializes a new [FirebaseApp](version /core/firebase-app) instance.

| Parameter |         |
| --------- | ------- |
| options   | **Object** |
| name   | **string** |

| Options |           |
| --------- | ------- |
| apiKey   | **string** |
| appId   | **string** |
| databaseURL   | **string** |
| messagingSenderId   | **string** |
| projectId   | **string** |
| storageBucket   | **string** |

### app
[method]app(name) returns [FirebaseApp](version /core/firebase-app);[/method]

Returns a [FirebaseApp](version /core/firebase-app) instance by name.

| Parameter |         |
| --------- | ------- |
| name   | **string** (optional) <br /> Returns the default app instance if no value. |

### setLogLevel
[method]setLogLevel(level) returns void;[/method]

Set the global logging level for all logs.

| Parameter |         |
| --------- | ------- |
| level   | **string** or **boolean** |

## Properties

### apps
[method]apps returns Array of [FirebaseApp](version /core/firebase-app);[/method]

Returns all initilized apps.

### SDK_VERSION
[method]SDK_VERSION returns string;[/method]

### DEFAULT_APP_NAME
[method]DEFAULT_APP_NAME returns string;[/method]

### googleApiAvailability
[method]googleApiAvailability returns Object;[/method]
