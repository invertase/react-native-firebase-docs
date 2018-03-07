# Introduction to Firebase Cloud Messaging

## Message Types

### Data-only messages

Data-only messages contain a map of key / value pairs and do not display any visible notification. As such, they will never be intercepted by the Mobile Device's OS.

Data-only messages are handled by the RNFirebase messaging module's `onMessageReceived` method.

Data-only messages behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | `onMessageReceived` triggered | `onMessageReceived` triggered  | `onMessageReceived` triggered |
| iOS     | `onMessageReceived` triggered | `onMessageReceived` triggered if `content_available` set to `true` | Received when app is next opened |


### Notification-only messages

Notification-only messages are used to display a visible notification on devices. They are intercepted by the Mobile Device's OS and will be delivered to the notification tray when the app is in the background or closed.

Notification-only messages are handled by the RNFirebase notifications module's `onNotificationReceived` and `onNotificationOpened` methods.

Notification-only messages behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | `onNotificationReceived` triggered | `onNotificationOpened` triggered if the notification is tapped | `getInitialNotification` is populated if the notification is tapped and opens the app |
| iOS     | `onNotificationReceived` triggered | `onNotificationReceived` triggered if `content_available` set to `true` <br />`onNotificationOpened` triggered if the notification is tapped | `getInitialNotification` is populated if the notification is tapped and opens the app |
| Notes   | No visible notification is shown to the user, it is up to you to display notifications manually | The notification is presented to the user by the Mobile Device's OS | The notification is presented to the user by the Mobile Device's OS |

### Notification + Data messages

Notification + Data messages are used to display a visible notification on devices with a data payload for consumption by the app. They are intercepted by the Mobile Device's OS and will be delivered to the notification tray when the app is in the background or closed.

Notification + Data messages are handled by the RNFirebase notifications module's `onNotificationReceived` and `onNotificationOpened` methods.

Notification + Data messages behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | `onNotificationReceived` triggered | `onNotificationOpened` triggered if the notification is tapped | `getInitialNotification` is populated if the notification is tapped and opens the app |
| iOS     | `onNotificationReceived` triggered | `onNotificationReceived` triggered if `content_available` set to `true` <br />`onNotificationOpened` triggered if the notification is tapped | `getInitialNotification` is populated if the notification is tapped and opens the app |
| Notes   | No visible notification is shown to the user, it is up to you to display notifications manually | The notification is presented to the user by the Mobile Device's OS | The notification is presented to the user by the Mobile Device's OS |