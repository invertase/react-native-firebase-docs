# Introduction to Firebase Cloud Messaging

Firebase Cloud Messaging allows remote messages to be delivered to your application.  There are a number of different message types which are explained in more detail below.

## Data-only messages

- Contain a map of key / value pairs for consumption by the app. 
- Do not display any visible notification.
- Never intercepted by the Mobile Device's OS.
- Handled by the RNFirebase Messaging module's `onMessageReceived` method.
- Behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | `onMessageReceived` triggered | `onMessageReceived` triggered  | `onMessageReceived` triggered |
| iOS     | `onMessageReceived` triggered | `onMessageReceived` triggered if `content_available` set to `true` | Received when app is next opened |


## Notification-only messages

- Used to display a visible notification on devices.
- Intercepted by the Mobile Device's OS.
- Delivered to the notification tray when the app is in the background or closed.
- Handled by the RNFirebase [Notifications module's](version /notifications/introduction) `onNotificationDisplayed`, `onNotificationReceived` and `onNotificationOpened` methods.
- Behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | `onNotificationReceived` triggered | `onNotificationOpened` triggered if the notification is tapped | `getInitialNotification` is populated if the notification is tapped and opens the app |
| iOS     | `onNotificationReceived` triggered | `onNotificationDisplayed` triggered if `content_available` set to `true` <br />`onNotificationOpened` triggered if the notification is tapped | `getInitialNotification` is populated if the notification is tapped and opens the app |
| Notes   | No visible notification is shown to the user, it is up to you to display notifications manually | The notification is presented to the user by the Mobile Device's OS | The notification is presented to the user by the Mobile Device's OS |

## Notification + Data messages

- Used to display a visible notification on devices.
- Contain a map of key / value pairs for consumption by the app if it is in the foreground, or if the notification is subsequently opened.  **If the notification is not opened, this data will never become available to the app.**
- Intercepted by the Mobile Device's OS.
- Delivered to the notification tray when the app is in the background or closed.
- Handled by the RNFirebase [Notifications module's](version /notifications/introduction) `onNotificationDisplayed`, `onNotificationReceived` and `onNotificationOpened` methods.
- Behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | `onNotificationReceived` triggered | `onNotificationOpened` triggered if the notification is tapped | `getInitialNotification` is populated if the notification is tapped and opens the app |
| iOS     | `onNotificationReceived` triggered | `onNotificationDisplayed` triggered if `content_available` set to `true` <br /><br />`onNotificationOpened` triggered if the notification is tapped | `getInitialNotification` is populated if the notification is tapped and opens the app |
| Notes   | No visible notification is shown to the user. You need to display a notification manually if this is required. | The notification is presented to the user by the Mobile Device's OS | The notification is presented to the user by the Mobile Device's OS |