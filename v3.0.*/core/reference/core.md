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

### apps

[method]apps returns Array of [ref core.FirebaseApp];[/method]

[collapse title=EXAMPLE]
```js
const foo = 'bar';

// test code
console.log(firebase.apps);

```
[/collapse]

Returns all initilized apps.

### SDK_VERSION
[method]SDK_VERSION returns string;[/method]

### DEFAULT_APP_NAME
[method]DEFAULT_APP_NAME returns string;[/method]

[collapse]

```js
console.log(firebase.DEFAULT_APP_NAME);
```
[/collapse]

### googleApiAvailability
[method]googleApiAvailability returns Object;[/method]
