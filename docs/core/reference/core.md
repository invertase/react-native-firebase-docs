# Core

## Methods

### initializeApp
[method]initializeApp(options, name) returns [ref core.FirebaseApp];[/method]

Initializes a new [ref core.FirebaseApp] instance.

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
[method]app(name) returns [ref core.FirebaseApp];[/method]

Returns a [ref core.FirebaseApp] instance by name.

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

### apps

[method]apps returns Array of [ref core.FirebaseApp];[/method]

Returns all initilized apps.


