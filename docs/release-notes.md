# v4.0.0-alpha Changelog

TL;DR: The one everybody has been waiting for: our overhaul of messaging and notification functionality to make it more reliable, better documented and easier to use.

Install using `npm install --save react-native-firebase@next`

Highlights:
- Better separation of concerns: `messaging`, `notifications` and `iid`
- Fully documented API
- Builder classes provide a type safe way to construct [messages](https://rnfirebase.io/docs/v4.0.x/messaging/reference/RemoteMessage) and [notifications](https://rnfirebase.io/docs/v4.0.x/notifications/reference/Notification)
- Clearer distinction between Android and IOS specific functionality
- Support for Android Notification Channels, Android Actions and Remote Input

TODO:
- Support for iOS notification categories

## An overview 

### Messaging vs Notifications

We have made the conscious decision to separate this functionality into two distinct areas:

- Messaging
  - handles remote FCM data-only messages
  - follows the official Firebase JS web SDK's messaging API where possible 

- Notifications
  - handles remote FCM notification and notification + data messages, 
  - handles the display and receipt of locally displayed notifications

You can read some more here: https://rnfirebase.io/docs/v4.0.x/messaging/introduction#Message-types

### Receiving messages and notifications

With our previous implementation, we had a single `onMessage` listener which was triggered for all messaging and notification actions, whether that was a notification in the foreground, background or even when the notification was pressed.  This meant you'd have to implement some logic to check the state of the notification to try and identify what had actually happened.

To simplify things, we've broken out a number of different listeners to provide greater control and customisation:

- Messaging
  - `onMessage`: Triggered when a data-only message is received remotely from FCM

Read more here: https://rnfirebase.io/docs/v4.0.x/messaging/receiving-messages

- Notifications
  - `onNotification`: Triggered when a remote of local notification is received
    - This will typically be triggered when your app is in the foreground
    - The notification will not have been displayed automatically to the end user by the OS, and it is up to you as the developer to display it if you wish to using `firebase.notifications().displayNotification()`: https://rnfirebase.io/docs/v4.0.x/notifications/displaying-notifications
  - `onNotificationDisplayed`: Triggered when a remote or local notification is displayed by the OS
    - This will typically be triggered when your app is in the background, or in the foreground if you have called `firebase.notifications().displayNotification()` directly.
    - The notification will have been displayed automatically to the end user by the OS
  - `onNotificationOpened`: Triggered when a remote or local notification is tapped / pressed / opened by the user
    - This will be triggered if your app is in the background or foreground
    - The event contains information about the notification and the action that the user took: https://rnfirebase.io/docs/v4.0.x/notifications/receiving-notifications#4)-Listen-for-a-Notification-being-opened
    - If your app is closed, then `firebase.notifications().getInitialNotification()` will be populated with this information when the app is started by a notification being opened.

Read more here: https://rnfirebase.io/docs/v4.0.x/notifications/receiving-notifications and https://rnfirebase.io/docs/v4.0.x/notifications/introduction

### Foreground vs Background

With our previous implementation, we relied on the `show_in_foreground` flag existing within the notification content to force the library to automatically show the notification if the app was running in the foreground.  Whilst this (kind of) worked, it meant it was down to the notification sender to control the display of the notification, not the app itself.

The `show_in_foreground` flag no longer exists and instead you can use the listeners described above to give better control, e.g.

```
firebase.notifications().onNotification((notification: Notification) => {
  // You've received a notification that hasn't been displayed by the OS
  // To display it whilst the app is in the foreground, simply call the following
  firebase.notifications().displayNotification(notification);
});
```

When the app is in the background, the OS will automatically handle the notification display when a remote or local notification is received.  If you wish to display a heads up notification on Android, we recommend you look at sending data only messages to your app.  These can be handled when your app is in the background or closed by following the instructions here: https://rnfirebase.io/docs/v4.0.x/messaging/receiving-messages#4)-(Optional)(Android-only)-Listen-for-FCM-messages-in-the-background

## Upgrade instructions

As you can imagine, this is a completely breaking change, so you'll want to follow the installation instructions available here:

- Messaging: [iOS](https://rnfirebase.io/docs/v4.0.x/messaging/ios) | [Android](https://rnfirebase.io/docs/v4.0.x/messaging/android)
- Notifications: [iOS](https://rnfirebase.io/docs/v4.0.x/notifications/ios) | [Android](https://rnfirebase.io/docs/v4.0.x/messaging/android)

There are a number of guides available: [Messaging](https://rnfirebase.io/docs/v4.0.x/messaging/introduction) | [Notifications](https://rnfirebase.io/docs/v4.0.x/notifications/introduction)

Reference can be found here: [Messaging](https://rnfirebase.io/docs/v4.0.x/messaging/reference/Messaging) | [Notifications](https://rnfirebase.io/docs/v4.0.x/notifications/reference/Notifications)

## Feedback

We want your feedback!!

If you have any comments and suggestions or want to report an issue, come find us on [Discord](https://discord.gg/C9aK28N)
