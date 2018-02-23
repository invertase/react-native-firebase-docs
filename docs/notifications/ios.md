# iOS Installation

First ensure you have followed the [initial setup guide](version /installation/initial-setup) and the [messaging setup guide](version /messaging/ios).

?> Notifications do not work on the iOS simulator, you must test is using a real device. This is a restriction enforced by Apple.

## Update `AppDelegate.m`

Add the following import to the top of your `ios/[App Name]/AppDelegate.m`:

```objectivec
#import "RNFirebaseNotifications.h"
```

Add the following to the `didFinishLaunchingWithOptions:(NSDictionary *)launchOptions` method, right after `[FIRApp Configure]`:

```objectivec
[RNFirebaseNotifications configure];
```

Add the following methods:

```objectivec
- (void)application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification {
  [[RNFirebaseNotifications instance] didReceiveLocalNotification:notification];
}

- (void)application:(UIApplication *)application didReceiveRemoteNotification:(nonnull NSDictionary *)userInfo
                                                       fetchCompletionHandler:(nonnull void (^)(UIBackgroundFetchResult))completionHandler{
  [[RNFirebaseNotifications instance] didReceiveRemoteNotification:userInfo fetchCompletionHandler:completionHandler];
}

- (void)application:(UIApplication *)application didRegisterUserNotificationSettings:(UIUserNotificationSettings *)notificationSettings {
  [[RNFirebaseMessaging instance] didRegisterUserNotificationSettings:notificationSettings];
}
```

## Debugging

If you're having problems with messages not being received, check out the following blog post for help:

https://firebase.googleblog.com/2017/01/debugging-firebase-cloud-messaging-on.html
