# iOS Installation

First ensure you have followed the [initial setup guide](version /installation/initial-setup).

?> FCM does not work on the iOS simulator, you must test is using a real device. This is a restriction enforced by Apple.

## Add the pod

Add the following to your `Podfile`:

```ruby
pod 'Firebase/Messaging'
```

Run `pod update`.

## Setup Certificates

Please follow the instructions on the [Firebase docs](https://firebase.google.com/docs/cloud-messaging/ios/certs) on how to setup your APN certificates with FCM.

## Enable Capabilities

In Xcode, enable the following capabilities:

1) Push Notifications
2) Background modes > Remote notifications

## Update `AppDelegate.h`

Add the following import to the top of your `ios/[App Name]/AppDelegate.h`:

```obj-c
@import UserNotifications;
```

Now change the interface descriptor to:

```obj-c
@interface AppDelegate : UIResponder <UIApplicationDelegate,UNUserNotificationCenterDelegate>
```

## Update `AppDelegate.m`

Add the following import to the top of your `ios/[App Name]/AppDelegate.m`:

```obj-c
#import "RNFirebaseMessaging.h"
```

Add the following to the `didFinishLaunchingWithOptions:(NSDictionary *)launchOptions` method after `[FIRApp Configure]`:

```obj-c
[[UNUserNotificationCenter currentNotificationCenter] setDelegate:self];
```

Add the following methods:

```objectivec
-(void)application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification {
  [RNFirebaseMessaging didReceiveLocalNotification:notification];
}

- (void)application:(UIApplication *)application didReceiveRemoteNotification:(nonnull NSDictionary *)userInfo {
  [RNFirebaseMessaging didReceiveRemoteNotification:userInfo];
}

- (void)application:(UIApplication *)application didReceiveRemoteNotification:(nonnull NSDictionary *)userInfo
fetchCompletionHandler:(nonnull void (^)(UIBackgroundFetchResult))completionHandler{
  [RNFirebaseMessaging didReceiveRemoteNotification:userInfo fetchCompletionHandler:completionHandler];
}

- (void)userNotificationCenter:(UNUserNotificationCenter *)center
       willPresentNotification:(UNNotification *)notification
         withCompletionHandler:(void (^)(UNNotificationPresentationOptions))completionHandler {
  [RNFirebaseMessaging willPresentNotification:notification withCompletionHandler:completionHandler];
}

- (void)userNotificationCenter:(UNUserNotificationCenter *)center
didReceiveNotificationResponse:(UNNotificationResponse *)response
         withCompletionHandler:(void (^)())completionHandler {
  [RNFirebaseMessaging didReceiveNotificationResponse:response withCompletionHandler:completionHandler];
}
```

## Debugging

If you're having problems with messages not being received, check out the following blog post for help:

https://firebase.googleblog.com/2017/01/debugging-firebase-cloud-messaging-on.html
