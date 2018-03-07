# Introduction to Firebase Cloud Messaging

## Message Types

### `Data` only messages

`Data` only messages contain a map of key / value pairs and do not display any visible notification. As such, they will never be intercepted by the Mobile Device's OS.

`Data` only messages are handled by the RNFirebase messaging module's `onMessageReceived` method.

`Data` only messages behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | Trigger `onMessageReceived` | Trigger `onMessageReceived`  | Trigger `onMessageReceived` |
| iOS     | Trigger `onMessageReceived` | Trigger `onMessageReceived` if `content_available` set to true | Received when app is next opened |


### `Notification` only messages

`Notification` only messages are used to display a visible notification on devices. They are intercepted by the Mobile Device's OS and will be delivered to the notification tray when the app is in the background or closed.

`Notification` only messages are handled by the RNFirebase notifications module's `onNotificationReceived` and `onNotificationOpened` methods.

`Notification` only messages behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | Trigger `onNotificationReceived` | Will only trigger `onNotificationOpened` if the notification is tapped | Will be handled by `getInitialNotification` if the notification is tapped to open the app |
| iOS     | Trigger `onNotificationReceived` | Will trigger `onNotificationReceived` if `content_available` set to true, and will trigger `onNotificationOpened` if the notification is tapped | Will be handled by `getInitialNotification` if the notification is tapped to open the app |
| ------- | --------------------------- | ---------------------------- | -----------|
| Notes   | No visible notification is shown to the user, it is up to you to display notifications manually | | |

### `Notification + Data` messages

`Notification + Data` only messages are used to display a visible notification on devices with a data payload for consumption by the app. They are intercepted by the Mobile Device's OS and will be delivered to the notification tray when the app is in the background or closed.

`Notification + Data` only messages are handled by the RNFirebase notifications module's `onNotificationReceived` and `onNotificationOpened` methods.

`Notification + Data` only messages behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | Trigger `onNotificationReceived` | Will only trigger `onNotificationOpened` if the notification is tapped | Will be handled by `getInitialNotification` if the notification is tapped to open the app |
| iOS     | Trigger `onNotificationReceived` | Will trigger `onNotificationReceived` if `content_available` set to true, and will trigger `onNotificationOpened` if the notification is tapped | Will be handled by `getInitialNotification` if the notification is tapped to open the app |
| ------- | --------------------------- | ---------------------------- | -----------|
| Notes   | No visible notification is shown to the user, it is up to you to display notifications manually | | |