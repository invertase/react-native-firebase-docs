# Analytics

```
firebase.analytics
```

## Methods

The following methods are accessed via the Analytics instance `firebase.analytics()`.

### logEvent
[method]logEvent(event, params) returns void;[/method]

Log a custom event with optional params.

[collapse Example]
```js
firebase.analytics().logEvent('add_to_cart', {
  id: '123',
  value: 100
});
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| event   | **string**  |
| params   | **object**  |

### setAnalyticsCollectionEnabled
[method]setAnalyticsCollectionEnabled(enabled) returns void;[/method]

If true, allows the device to collect analytical data and send it to Firebase.

[collapse Example]
```js
firebase.analytics().setAnalyticsCollectionEnabled(false);
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| enabled   | **boolean**  |

### setCurrentScreen
[method]setCurrentScreen(screenName, screenClassOverride) returns void;[/method]

Sets the current screen name.

?> Whilst `screenClassOverride` is optional, it is recommended it is always sent as your current class name, for example on Android it will always show as 'MainActivity' if not specified.

[collapse Example]
```js
firebase.analytics().setCurrentScreen('Homepage', 'App');
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| screenName   | **string**  |
| screenClassOverride   | **string** (optional)  |

### setMinimumSessionDuration
[method]setMinimumSessionDuration(miliseconds) returns void;[/method]

Sets the minimum engagement time required before starting a session. The default value is 10000 (10 seconds).

[collapse Example]
```js
firebase.analytics().setMinimumSessionDuration(20000);
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| miliseconds   | **number**  |

### setSessionTimeoutDuration
[method]setSessionTimeoutDuration(miliseconds) returns void;[/method]

Sets the duration of inactivity that terminates the current session. The default value is 1800000 (30 minutes).

[collapse Example]
```js
firebase.analytics().setMinimumSessionDuration(900000);
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| miliseconds   | **number**  |

### setUserId
[method]setUserId(id) returns void;[/method]

Gives a user a unique identification.

[collapse Example]
```js
const user = firebase.auth().currentUser;
firebase.analytics().setUserId(user.uid);
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| id   | **string**  |

### setUserProperty
[method]setUserProperty(name, value) returns void;[/method]

Sets a key/value pair of data on the current user.

[collapse Example]
```js
firebase.analytics().setUserProperty('age', 18);
```
[/collapse]


| Parameter |         |
| --------- | ------- |
| name   | **string**  |
| value   | **string**  |
