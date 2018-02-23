# Notifications

## Methods

The following methods are accessed via the Cloud Messaging instance firebase.messaging().
### getInitialNotification
[method]getInitialNotification() returns Promise containing Object;[/method]

When the application has been opened from a notification, `getInitialNotification` is called and the notification payload is returned. Use [ref messaging#onMessage] for notifications when the app is running.

### deleteInstanceId
[method]deleteInstanceId() returns Promise containing void;[/method]

Reset Instance ID and revokes all tokens.

### onTokenRefresh
[method]onTokenRefresh(listener) returns function();[/method]

On the event a devices FCM token is refreshed by Google, the new token is returned in a callback listener.

Returns an unsubscribe function.

| Parameter |         |
| --------- | ------- |
| listener   | **function(string)** <br /> A listener function called when a new token is generated. |

### cancelLocalNotification
[method]cancelLocalNotification(id) returns void;[/method]

Cancels a location notification by ID, or all notifications by *.

### removeDeliveredNotification
[method]removeDeliveredNotification(id) returns void;[/method]

Removes all delivered notifications from device by ID, or all notifications by *.

### [ios] requestPermissions
[method]requestPermissions() returns Promise<Object>;[/method]

Requests app notification permissions in an Alert dialog. 

On iOS 9 or below, there's no way to tell whether the user accepted or rejected the permissions popup - in this case the resolved object will have a property called `status` with a value of `"unknown"`

In all other cases the resolved object will have a `granted` property which is a boolean value of `true` or `false`.

On iOS 9 or below, there's no way to tell whether the user accepted or rejected the permissions popup - in this case the resolved object will have a property called `status` with a value of `"unknown"`

In all other cases the resolved object will have a `granted` property which is a boolean value of `true` or `false`.

### setBadgeNumber
[method]setBadgeNumber(value) returns void;[/method]

Sets the badge number on the app icon.

| Parameter |         |
| --------- | ------- |
| value   | **number**  |

### getBadgeNumber
[method]getBadgeNumber() returns Promise containing number;[/method]

Returns the current badge number on the app icon.