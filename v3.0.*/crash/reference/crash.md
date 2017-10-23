# Crash Reporting

```
firebase.crash
```

## Methods 

The following methods are accessed via the Crash instance `firebase.crash()`.

### setCrashCollectionEnabled
[method]setCrashCollectionEnabled(enabled) returns void;[/method]

Enables or disables crash reporting. 

[collapse Example]
```js
firebase.crash().setCrashCollectionEnabled(false);
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| enabled   | **boolean** <br />Whether crash reporting is enabled or disabled |

### isCrashCollectionEnabled
[method]isCrashCollectionEnabled() returns Promise containing boolean;[/method]

Returns whether crash reporting is currently enabled or disabled.

[collapse Example]
```js
firebase.crash().isCrashCollectionEnabled();
  .then((isEnabled) => {
    console.log('Crash reporting is enabled: ', isEnabled);
  });
```
[/collapse]

### log
[method]log(message) returns void;[/method]

Logs a message that will be sent with a [ref crash#report].

[collapse Example]
```js
firebase.crash().log('Something went really wrong!');
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| message   | **string** |

### logcat
[method]logcat(level, tag, message) returns void;[/method]

[android] Logs a message that will appear in a subsequent crash report as well as in [logcat](https://developer.android.com/studio/command-line/logcat.html).
[ios] Logs the message in the subsequest crash report only (same as log).

[collapse Example]
```js
firebase.crash().logcat(1, 'CRASH', 'Something went really wrong!');
```
[/collapse]

| Parameter |     |
| --------- | --- |
| level     | **number** |
| tag       | **string** |
| message   | **string** |

### report
[method]report(error, maxStackSize) returns void;[/method]

Sends the crash report, along with any previous [ref crash#log] or [ref crash#logcat] to Firebase.

> Reports are not realtime. They can take a number of hours to appear in the Firebase console.

[collapse Example]
```js
try {
  loadSomeService();
} catch(e) {
  firebase.crash().log('Service failed to load');
  firebase.crash().report(e, 10);
}
```
[/collapse]

| Parameter |     |
| --------- | --- |
| error     | [**Error**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error) <br /> A JavaScript Error. |
| maxStackSize | **number** |
