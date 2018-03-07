# Introduction to Firebase Cloud Messaging

Firebase Cloud Messaging allows messages and notifications to be delivered to your application remotely.

To try and keep things simple and easier to understand, we have divided the React Native Firebase functionality clearly between data-only and notification messages.

This module deals exclusively with data-only messages.

> For notification-only and notification + data FCM messages please see the [Notifications module](version /notifications/introduction).

## Data-only messages

- Handled by the RNFirebase Messaging module.
- Contain a data payload (map of key / value pairs) for consumption by the app. 
- Do not display any visible notification.
- Never intercepted by the Mobile Device's OS.
- Behave as follows:

|         | App in foreground           | App in background            | App closed |
| ------- | --------------------------- | ---------------------------- | -----------|
| Android | `onMessageReceived` triggered | `onMessageReceived` triggered  | `onMessageReceived` triggered |
| iOS     | `onMessageReceived` triggered | `onMessageReceived` triggered if `content_available` set to `true` | Received when app is next opened |


## Notification-only and Notification + Data messages

- Handled by the RNFirebase [Notifications module](version /notifications/introduction).
- Used to display a visible notification on devices.
- Contain an optional data payload (map of key / value pairs) for consumption by the app if it is in the foreground, or if the notification is subsequently opened.  **If the notification is not opened, this data will never become available to the app.**
- Intercepted by the Mobile Device's OS.
- Delivered to the notification tray when the app is in the background or closed.
- Behaviour is defined in the [Notifications module](version /notifications/introduction).
