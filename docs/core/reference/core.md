# Core

## Methods

### initializeApp
[method]initializeApp(options, name) returns [ref core.App];[/method]

Initializes a new [ref core.App] instance.

[collapse Parameters]

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

[/collapse]

### app
[method]app(name) returns [ref core.App];[/method]

Returns a [ref core.App] instance by name.

[collapse Parameters]

| Parameter |         |
| --------- | ------- |
| name   | **string** (optional) <br /> Returns the default app instance if no value. |

[/collapse]


### setLogLevel
[method]setLogLevel(level) returns void;[/method]

Set the global logging level for all logs.

[collapse Parameters]

| Parameter |         |
| --------- | ------- |
| level   | **string** or **boolean** |

[/collapse]

## Properties

### apps

[method]apps returns Array of [ref core.App];[/method]

Returns all initilized apps.


