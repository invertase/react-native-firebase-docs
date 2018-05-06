# Migration Guide - v3 to v4

The below is a quick summary of steps to take when migrating from v3 to v4 of RNFirebase. Please see the [v4 change log](https://github.com/invertase/react-native-firebase/releases/tag/v4.0.0) for detailed changes.

## 1) Install the latest version of RNFirebase:

```
npm install react-native-firebase@latest --save`
```

## 2) Android

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

3) In `android/build.gradle` update Android build tools to version `{{ android.build.tools }}`:

```groovy
classpath 'com.android.tools.build:gradle:{{ android.build.tools }}'
```

4) In `android/app/build.gradle` update all your `compile` statements to be `implementation`, e.g.

```groovy
implementation(project(':react-native-firebase')) {
    transitive = false
}
```

5) In `android/app/build.gradle`, update all the firebase and gms dependencies to the following versions:

- **com.google.android.gms:play-services-base**: {{ android.gms.play-services-base }}
- **com.google.firebase:firebase-core**: {{ android.firebase.core }}
- **com.google.firebase:firebase-ads**: {{ android.firebase.ads }}
- **com.google.firebase:firebase-auth**: {{ android.firebase.auth }}
- **com.google.firebase:firebase-config**: {{ android.firebase.config }}
- **com.google.firebase:firebase-crash**: {{ android.firebase.crash }}
- **com.google.firebase:firebase-database**: {{ android.firebase.database }}
- **com.google.firebase:firebase-invites**: {{ android.firebase.invites }}
- **com.google.firebase:firebase-firestore**: {{ android.firebase.firestore }}
- **com.google.firebase:firebase-messaging**: {{ android.firebase.messaging }}
- **com.google.firebase:firebase-perf**: {{ android.firebase.perf }}
- **com.google.firebase:firebase-storage**: {{ android.firebase.storage }}
- **com.crashlytics.sdk.android:crashlytics**:  {{ android.firebase.crashlytics }}

6) When running your app from within Android Studio, you may encounter `Missing Byte Code` errors.  This is due to a known issue with version 3.1.x of the android tools plugin: https://issuetracker.google.com/issues/72811718.  You'll need to disable Instant Run to get past this error.

## 3) Module-specific instructions

### Messaging / Notifications

As you can imagine, for Messaging and Notifications this is a completely breaking change, so you'll want to follow the installation instructions available here:

- Messaging: [iOS](https://rnfirebase.io/docs/v4.0.x/messaging/ios) | [Android](https://rnfirebase.io/docs/v4.0.x/messaging/android)
- Notifications: [iOS](https://rnfirebase.io/docs/v4.0.x/notifications/ios) | [Android](https://rnfirebase.io/docs/v4.0.x/notifications/android)

There are a number of guides available: [Messaging](https://rnfirebase.io/docs/v4.0.x/messaging/introduction) | [Notifications](https://rnfirebase.io/docs/v4.0.x/notifications/introduction)

Reference can be found here: [Messaging](https://rnfirebase.io/docs/v4.0.x/messaging/reference/Messaging) | [Notifications](https://rnfirebase.io/docs/v4.0.x/notifications/reference/Notifications)

Some key things to note:

- The iOS `AppDelegate.m` will need to be completely updated
- All packages in `AndroidManifest.xml` will need to be updated
- `firebase.messaging().requestPermissions()` is now `firebase.messaging().requestPermission()`
- `firebase.messaging().setBadgeNumber()` and `firebase.messaging().getBadgeNumber()` are now `firebase.notifications().setBadge()` and `firebase.notifications().getBadge()`

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

## 4) iOS - Update podfile:

- You need to check that you're running at least version 4.11.0 of the Firebase Pods
  - Run `pod outdated`
  - Run `pod update`
