# v4.0.0 Changelog

TL;DR: The one everybody has been waiting for: our overhaul of messaging and notification functionality to make it more reliable, better documented and easier to use.

Plus, we've got Firebase Invites, Multi-Database url support, an overhaul of Dynamic Links and some other minor fixes.

**Notification highlights:**
- Better separation of concerns: `messaging`, `notifications` and `instanceid`
- Fully documented API
- Builder classes provide a type safe way to construct [messages](https://rnfirebase.io/docs/v4.0.x/messaging/reference/RemoteMessage) and [notifications](https://rnfirebase.io/docs/v4.0.x/notifications/reference/Notification)
- Clearer distinction between Android and IOS specific functionality
- Support for Android Notification Channels, Android Actions and Remote Input
- Support for BigTextStyle and BigPictureStyle Android notifications

**Outstanding functionality (to be added in a later release):**
- Support for iOS notification categories

----

## Quick Start

Install using:
 
```
npm install --save react-native-firebase
```

----

## Messaging 

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

```js
firebase.notifications().onNotification((notification: Notification) => {
  // You've received a notification that hasn't been displayed by the OS
  // To display it whilst the app is in the foreground, simply call the following
  firebase.notifications().displayNotification(notification);
});
```

When the app is in the background, the OS will automatically handle the notification display when a remote or local notification is received.  If you wish to display a heads up notification on Android, we recommend you look at sending data only messages to your app.  These can be handled when your app is in the background or closed by following the instructions here: https://rnfirebase.io/docs/v4.0.x/messaging/receiving-messages#4)-(Optional)(Android-only)-Listen-for-FCM-messages-in-the-background

----

## Firebase Invites

We've added full support for Firebase Invites: [iOS](https://rnfirebase.io/docs/v4.0.x/invites/ios) | [Android](https://rnfirebase.io/docs/v4.0.x/invites/android)

----

## Dynamic Links

We've rolled out the `Builder` approach to Dynamic Links.  Check out the [createDynamicLink](https://rnfirebase.io/docs/v4.0.x/links/reference/links#createDynamicLink) docs and [Dynamic Link](https://rnfirebase.io/docs/v4.0.x/links/reference/DynamicLink) reference docs

!> This is a breaking change.

----

## Cloud Firestore

- Added support for `disableNetwork` and `enableNetwork`
- Added typescript definitions for Transactions

----

## Authentication

- Fixed issue with null photo URL when updating a user profile #911

----

## Database

- Fixed issue with server time offset #910
- Database now supports using multiple database instances via database urls e.g.:
```js
const dbShard = firebase.database('https://rnfirebase-3.firebaseio.com/');
```
> Big shout out to @akshetpandey and @Chenjh1992 for their help getting this pushed through on #881 

## Crashlytics

- Crashlytics now lives at the top level under `firebase.crashlytics()`

----

## Upgrade instructions

```
npm install --save react-native-firebase@latest
```

### Gradle

Due to some breaking changes in v12 of the Android libs, you'll need to upgrade your Gradle version to at least v4.4 and make a few other tweaks as follows:

1) In `android/gradle/wrapper/gradle-wrapper.properties`, update the gradle URL to `gradle-4.4-all.zip`
2) In `android/build.gradle` check that you have `google()` specified in the buildScript repositories section:

```groovy
buildscript {
    repositories {
        jcenter()
        google()  // <-- Check this line exists
        ...
    }
```

3) In `android/build.gradle` update Android build tools to version `3.1.0`:

```groovy
classpath 'com.android.tools.build:gradle:3.1.0'
```

4) In `android/app/build.gradle` update all your `compile` statements to be `implementation`, e.g.

```groovy
implementation(project(':react-native-firebase')) {
    transitive = false
}
```

5) In `android/app/build.gradle`, update all the firebase and gms dependencies to 12.0.1

6) When running your app from within Android Studio, you may encounter `Missing Byte Code` errors.  This is due to a known issue with version 3.1.0 of the android tools plugin: https://issuetracker.google.com/issues/72811718.  You'll need to disable Instant Run to get past this error.

### Messaging / Notifications

As you can imagine, for Messaging and Notifications this is a completely breaking change, so you'll want to follow the installation instructions available here:

- Messaging: [iOS](https://rnfirebase.io/docs/v4.0.x/messaging/ios) | [Android](https://rnfirebase.io/docs/v4.0.x/messaging/android)
- Notifications: [iOS](https://rnfirebase.io/docs/v4.0.x/notifications/ios) | [Android](https://rnfirebase.io/docs/v4.0.x/messaging/android)

There are a number of guides available: [Messaging](https://rnfirebase.io/docs/v4.0.x/messaging/introduction) | [Notifications](https://rnfirebase.io/docs/v4.0.x/notifications/introduction)

Reference can be found here: [Messaging](https://rnfirebase.io/docs/v4.0.x/messaging/reference/Messaging) | [Notifications](https://rnfirebase.io/docs/v4.0.x/notifications/reference/Notifications)

### Dynamic Links

- For dynamic links on iOS, you need to make a subtle change to your `AppDelegate.m`:

```objectivec
- (BOOL)application:(UIApplication *)application
            openURL:(NSURL *)url
            options:(NSDictionary<NSString *, id> *)options {
    return [[RNFirebaseLinks instance] application:application openURL:url options:options];
}

- (BOOL)application:(UIApplication *)application
continueUserActivity:(NSUserActivity *)userActivity
 restorationHandler:(void (^)(NSArray *))restorationHandler {
     return [[RNFirebaseLinks instance] application:application continueUserActivity:userActivity restorationHandler:restorationHandler];
}
```

### Crashlytics

- All Crashlytics methods have been moved from `firebase.fabric.crashlytics()` to `firebase.crashlytics()`

### Crash Reporting

- Crash reporting is now flagged as deprecated.  We recommend you upgrade to Crashlytics which is now Firebase's recommended crash tool.

----

## Feedback

We want your feedback!!

If you have any comments and suggestions or want to report an issue, come find us on [Discord](https://discord.gg/C9aK28N)
