# Release Notes

## 5.1.1

This patch release is mainly to fix several minor typings issues (TS & Flow). 

Thanks to all our [contributors](https://github.com/invertase/react-native-firebase/compare/v5.1.0...v5.1.1). 💛

You can compare all changes between v5.1.0 and v5.1.1 [here](https://github.com/invertase/react-native-firebase/compare/v5.1.0...v5.1.1).

### Upgrade from v5.1.0

No native code or dependency version changes required. Install the latest version via NPM:
 
```bash
npm install --save react-native-firebase@5.1.1
```

----

### General

- [TYPESCRIPT] [ENHANCEMENT] [ANALYTICS] Add `setUserProperties` type definition
- [TYPESCRIPT] [ENHANCEMENT] [AUTHENTICATION] Improve TS types for auth listeners
- [TYPESCRIPT] [ENHANCEMENT] [STORAGE] Export storage statics (`.Native`, `.TaskState` and `.TaskEvent`) - fixes #1706
- [TYPESCRIPT] [ENHANCEMENT] [FIRESTORE] Improve `onSnapshot` error type definitions - fixes #1708
- [FLOW] [BUGFIX] [LINKS] Change return type to `string` literal instead of incorrect usage of `String`
- [TESTS] [ENHANCEMENT] [DATABASE] Improve query test coverage 
 
----

### Android

- [ANDROID] [BUGFIX] [NOTIFICATIONS] Added missing input text result field to `notificationOpen` object
- [ANDROID] [ENHANCEMENT] [BUILD] Update build script to also read Android sources from `react-native` root directory - fixes #1697 

----

### iOS

- [IOS] [BUGFIX] [AUTHENTICATION] `authStateChanged` listeners now correctly torn down between RN reloads - fixes #1677

----

----

## 5.1.0

This release is mainly focused on bug fixes and QoL changes with only some minor enhancements added such as Firestore `arrayRemove`/`arrayUnion` support.

Thanks to all our [contributors](https://github.com/invertase/react-native-firebase/compare/v5.0.0...v5.1.0-rc3). 💛

### Upgrade from v5.0.0

Install the latest version:
 
```bash
npm install --save react-native-firebase@5.1.0
```

----

Update native dependencies:

?> Please ensure you change your versions to match the ones below (where possible).

 - [IOS] Updated Firebase SDKs (Pods) to `v5.11.0` - `v5.10.0` is also supported
 - [ANDROID] Updated gradle build tools to `3.2.0`
     - `classpath 'com.android.tools.build:gradle:3.2.0'`
 - [ANDROID] Updated default build tools version to `28.0.2`
 - [ANDROID] Updated `play-services-base` to `16.0.1`
 - [ANDROID] Updated Firebase SDKs;
   - see [/tests/android/app/build.gradle](https://github.com/invertase/react-native-firebase/blob/master/tests/android/app/build.gradle) for a reference app build gradle file


```groovy
implementation "com.google.firebase:firebase-core:16.0.4"
implementation "com.google.android.gms:play-services-base:16.0.1"

/* -------------------------
*   OPTIONAL FIREBASE SDKS
* ------------------------- */

implementation('com.google.firebase:firebase-ads:15.0.1') {
    // exclude `customtabs` as the support lib version is out of date
    // we manually add it as a dependency below with a custom version
    exclude group: 'com.android.support', module: 'customtabs'
}

// Authentication
implementation "com.google.firebase:firebase-auth:16.0.5"

// Analytics
implementation "com.google.firebase:firebase-analytics:16.0.4"

// Performance Monitoring
implementation "com.google.firebase:firebase-perf:16.2.0"

// Remote Config
implementation "com.google.firebase:firebase-config:16.1.0"

// Cloud Storage
implementation "com.google.firebase:firebase-storage:16.0.4"

// Invites
implementation "com.google.firebase:firebase-invites:16.0.4"

// Dynamic Links
implementation "com.google.firebase:firebase-dynamic-links:16.1.2"

// Real-time Database
implementation "com.google.firebase:firebase-database:16.0.4"

// Cloud Functions
implementation "com.google.firebase:firebase-functions:16.1.2"

// Cloud Firestore
implementation "com.google.firebase:firebase-firestore:17.1.2"

// Cloud Messaging / FCM
implementation "com.google.firebase:firebase-messaging:17.3.4"

// Crashlytics
implementation('com.crashlytics.sdk.android:crashlytics:2.9.5@aar') {
    transitive = true
}

/* --------------------------------
*  OPTIONAL SUPPORT LIBS
* -------------------------------- */

// For Firebase Ads
implementation "com.android.support:customtabs:27.1.1"

// For React Native Firebase Notifications
implementation 'me.leolin:ShortcutBadger:1.1.21@aar'
```

----

 - [ANDROID] Update build dependencies;
   - see [/tests/android/build.gradle](https://github.com/invertase/react-native-firebase/blob/master/tests/android/build.gradle) for a reference project build gradle file

```groovy
classpath 'com.android.tools.build:gradle:3.2.0'
classpath 'com.google.gms:google-services:4.0.1'
classpath 'com.google.firebase:firebase-plugins:1.1.5'
classpath 'io.fabric.tools:gradle:1.25.4'
```

----

 - [ANDROID] Updated to gradle 4.6

 You can update your gradle version if required by adding the following at the bottom of your `/android/build.gradle`

```groovy
task wrapper(type: Wrapper) {
    gradleVersion = '4.6'
    distributionUrl = distributionUrl.replace("bin", "all")
}
```

 Or by modifying the `distributionUrl` in `/android/gradle/wrapper/gradle-wrapper.properties`
 
----

### General

 - [JS] [INTERNAL] [BUGFIX] [./utils/native.js] - `nativeWithArgs` wrapper incorrectly wrapping `NativeModule` constants - should only wrap functions.
 - [ANDROID] [BUILD] force Java 8 target compatibility for JDK 10 - #1070
 - [ANDROID] [BUILD] add support for reading React Native sources from inside a mono-repo
 - [ANDROID] [BUILD] remove fabric build tools from lib - only needed in users build.gradle
 - [ANDROID] replace `android.support`.`NonNull` & `Nullable` annotation instances with java annotations
    - removes dependency on android support v4 annotations
 - [ANDROID] [IOS] [CORE] added `firebase.app().delete()` support (was pending Android SDK support which has now been added)
 - [LINKS] [TS] fix types for `createShortDynamicLink` - #1580
 - [FUNCTIONS] [TS] add export of `functions` type #1533
 - [METRO] [JS] add workaround for `module-resolver` bug - #1560
 
----

### Authentication

```js
firebase.auth()
```

 - [IOS] [ANDROID] [BUGFIX] - `currentUser` now persisted and correctly available between React Native reloads (also applies to code push reloads). Fixes [#1568](https://github.com/invertase/react-native-firebase/issues/1568).
 - [IOS] [ANDROID] [BUGFIX] - `AuthState` and `IdToken` listeners now correctly teardown between React Native reloads (also applies to code push reloads).
 - [IOS] [ENHANCEMENT] - Added new iOS SDK Auth error codes for mapping to JS SDK error codes. Fixes #1418.

----

### Cloud Firestore

```js
firebase.firestore()
```

 - [ANDROID] [IOS] [ENHANCEMENT] add `arrayRemove` and `arrayUnion` support for `FieldValue`. [#1624](https://github.com/invertase/react-native-firebase/pull/1624)
 - [IOS] improve/rework native transaction code to prevent potential race conditions while locally developing. #1556

----

### Database

```js
firebase.database()
```

 - [ANDROID] fix transaction failure issue when paused in chrome debugger [#1503](https://github.com/invertase/react-native-firebase/issues/1503)
 - [ANDROID] [BUGFIX] - Database listeners now correctly tearing down between RN reloads. (Fixes #1498 #1611 #1609)
 - [JS] [BUGFIX] - Fixed an issue where `Reference.toString()` incorrectly contains `//` instead of `/` when joining the parent and child paths.
 - [JS] [BUGFIX] - Rework `.push()` behaviour to match WebSDK and correctly return a Reference instance in all scenarios. (Fixes #893 #1464 #1572)
 - [JS] [ENHANCEMENT] [UTILS] - Added a `firebase.utils().database.cleanup()` utility method which removes all database listeners.
 - [JS] [ENHANCEMENT] - Added support for the Web SDK's `snapshot.exportVal()` method. Fixes [#1497](https://github.com/invertase/react-native-firebase/issues/1497).
 - [JS] add Reference.`toJSON()` support to match the Web SDK

----

### Messaging & Notifications

```js
firebase.messaging()
firebase.notifications()
```

 - [IOS] [FEATURE] [MESSAGING] - Add `IOSMessaging` module for `APNS` specific methods. [#1626](https://github.com/invertase/react-native-firebase/pull/1626)
   - `firebase.messaging().ios.getAPNSToken(): Promise<string | null>`
   - `firebase.messaging().ios.registerForRemoteNotifications(): Promise<void>`
 - [TYPES] [BUGFIX] [NOTIFICATIONS] - Change `IOSNotification` badge type definition to number.
 - [NOTIFICATIONS] [IOS] fixed a crash when 'completing' a notification #1576.
 - [NOTIFICATIONS] [ANDROID] fixed multiple `NoSuchMethodError` exceptions on `< API 26`. #1550 #1549 #1553 #1399
 - [NOTIFICATIONS] [ANDROID] `DisplayNotificationTask` now correctly uses `WeakReference` to keep ref to `Context`
 - [NOTIFICATIONS] [ANDROID] `removeDeliveredNotificationsByTag` now correctly removes. #1546
 - [NOTIFICATIONS] [ANDROID] fixed a `removeDeliveredNotificationsByTag` crash. #1392


----

### Storage

```js
firebase.storage()
```

 - [ANDROID] [BUGFIX] - Writable only locations (via storage rules) now successfully resolve their upload tasks without trying to read the `downloadUrl` afterwards (formerly caused a `ERROR_NOT_AUTHORIZED` exception). Fixes [#1591](https://github.com/invertase/react-native-firebase/issues/1591)



----

----

----

----

----

## 5.0.0

Install using:
 
```bash
npm install --save react-native-firebase@latest
```


### General

 - Remove `fbjs` peer dependency
 - Update Flow version: `^0.78.0`
 - Update TypeScript version: `^3.0.3`
 - Support React Native versions `^0.56.0` to `^0.57.0`
 - Remove bloated `opencollective` install only dependency
 - Remove formerly deprecated Crash Reporting (`firebase.crash()`)
 - Update build script to Babel 7 & [`@invertase/babel-preset-react-native-syntax`](https://github.com/invertase/babel-preset-react-native-syntax)
 - Add support for import destructuring e.g. `import { database } from 'react-native-firebase'`
 - Remove internal clone of React Natives JS event emitter - now points to exposed version from React Native directly - [dbe2673](https://github.com/invertase/react-native-firebase/commit/dbe2673bc637b921ad334c900da88ca1a90d3709)
 - [android][internals] `Utils.isAppInForeground` not correctly accounting for RN LifecycleState;
   - this utility in some rare cases would return true that Activity was in the foreground, however, React Native was still in the process of resuming, this, for example, led to crashes in HeadlessJS Notification tasks: `"Tried to start task RNFirebaseBackgroundMessage while in foreground, but this is not allowed."`

----

### Authentication

```js
firebase.auth()
```

 - Add support for [ref auth.AuthSettings] - allows for automated testing phone authentication flows in your test suites/CI.
    - Guide: [Test with whitelisted phone numbers](https://firebase.google.com/docs/auth/web/phone-auth#test-with-whitelisted-phone-numbers)
 - Add support for [ref auth.User#getIdTokenResult];
    - Guide: [Firebase - Control Access with Custom Claims and Security Rules](https://firebase.google.com/docs/auth/admin/custom-claims)
    - YouTube - Firecasts: [Controlling Data Access Using Firebase Auth Custom Claims](https://youtu.be/3hj_r_N0qMs)
 - Add support for [ref auth.User#updatePhoneNumber]
 - Remove formerly deprecated method `getToken` - use [ref auth.User#getIdToken] or [ref auth.User#getIdTokenResult] instead
 - Deprecated all `*AndRetrieveData*` `auth()` and `auth().currentUser` methods;
    - e.g. `signInAndRetrieveDataWithEmailAndPassword` is now deprecated and `signInWithEmailAndPassword` undeprecated with the output of `signInWithEmailAndPassword` becoming that of `signInAndRetrieveDataWithEmailAndPassword`. The same applies to all the other AndRetrieveData methods.
 - [ref auth.ActionCodeInfo#operation] now correctly returned - native code was incorrectly returning a key named `actionType`
   - Additionally added the `EMAIL_SIGNIN` type

----

### Cloud Firestore

```js
firebase.firestore()
```

#### All Platforms

 - Add support for `'array-contains'` querying
   - Guide: [Better Arrays in Cloud Firestore!](https://firebase.googleblog.com/2018/08/better-arrays-in-cloud-firestore.html)
     - `arrayUnion` & `arrayRemove` support coming soon
 - Add support for `NaN` and `Infinity` values in documents - [#1357](https://github.com/invertase/react-native-firebase/issues/1357)
 - Document & Query snapshot listeners now correctly returns an Error class instance on error, formerly returned a plain object
   - Instance of [ref firestore.SnapshotError]
 - Collection / Document listeners now internally handle errors even if no error observer provided
   -  Additionally now self-unsubscribes listeners on JS and Native if an error occurs, not leaving them in limbo

#### Android

 - `AsyncTask` serialize Document/Query snapshots to reduce UI/FPS lag - [#1223](https://github.com/invertase/react-native-firebase/issues/1223)
  - [Before & After change UI lag comparison video](https://drive.google.com/file/d/121Ouk57Ai29atadSdt_klILtDy1iTEhO/view)

----

### Cloud Functions

```js
firebase.functions()
```

 - Add support for specifying a custom function region, e.g. `us-central1`
 - Add support for multiple Firebase app instances, e.g. `firebase.app('someOtherApp').functions()`
 - Add support for [ref functions.Functions#useFunctionsEmulator], e.g. run a Cloud Functions emulator locally and point your app to it
   - Guide: [Functions - Local Emulator](https://firebase.google.com/docs/functions/local-emulator)
 - [ref functions.HttpError] now correctly extends `Error` - was a Babel issue formerly blocking this

**Examples:**

```js
// default app and region
const functions = firebase.functions();
// custom FirebaseApp
const functions = firebase.functions(app);
// custom region
const functions = firebase.functions('us-central1');
// custom FirebaseApp and region
const functions = firebase.functions(app, 'us-central1');

// cloud functions local emulator support
// see https://firebase.google.com/docs/functions/local-emulator
const origin = 'http://localhost:3000';
await functions.useFunctionsEmulator(origin);
```

----

### Crashlytics

```js
firebase.crashlytics()
```

#### iOS

 - Fix for `module not initialized` errors when using Crashlytics via manual linking (without Pods)
   - Commit: [e20652](https://github.com/invertase/react-native-firebase/commit/e20652d67d36e5045fe6ca6c6a6f5567ac40f5a7)

----

### Database

```js
firebase.database()
```

#### Android

 - [internal] Transactions now correctly reset signalled state on every transaction attempt
   - To address "already signalled" exceptions

----

### Dynamic Invites

```js
firebase.invites()
```

#### Android

 - Fix Invites module error `"requestCode must be in 16 bits"`

----


### Messaging 

#### All Platforms

 - Add [ref messaging#deleteToken] support - requires [ref iid]()
 
#### iOS

 - Add support for Background notification completion handlers - [#1393](https://github.com/invertase/react-native-firebase/pull/1393)
 - Fix for [ref messaging.Messaging#getToken] resolving null if called early on in app initialization
    - Commit: [66aa5cc](https://github.com/invertase/react-native-firebase/commit/66aa5ccb67356bc22ef27507c93be737d1871b4b#diff-06c99e7e87036c83640e069ed3ddea7e)

----

### Notifications 

#### Android

 - Fix `Null Pointer Exception` crash caused by calling `deleteChannelGroup` on a `channelId` that does not exist
 - Fix `createChannelGroups` issue - native method incorrectly named
 - Fix a crash that occurred when using `vibrationPattern` - native array not initialized with the correct size
 - Fix issue with alert once notification behavior - native was incorrectly calling `setOngoing` instead of `setOnlyAlertOnce`
 - Notifications now uses localized title and body from remote messages (e.g. `title_loc_key`) if `title` or `body` are not specified

#### iOS

 - Add support for Background notification completion handlers - [#1393](https://github.com/invertase/react-native-firebase/pull/1393)

----

### Performance Monitoring 

 - Add support for custom [ref perf-mon.Trace] attributes
   - Guide: [Monitor Custom Attributes](https://firebase.google.com/docs/perf-mon/custom-attributes)
   - **Methods**:
       - [ref perf-mon.Trace#getAttribute]
       - [ref perf-mon.Trace#getAttributes]
       - [ref perf-mon.Trace#putAttribute]
       - [ref perf-mon.Trace#removeAttribute]
 - Add support for [ref perf-mon.HttpMetric]'s
 - **BREAKING**: `Trace#incrementCounter` has been removed. See [ref perf-mon.Trace#incrementMetric] for a replacement.

----

### Remote Config 

 - Allow handling Remote config throttled exceptions, e.g. rejects with code `"config/throttled"` - [#1295](https://github.com/invertase/react-native-firebase/pull/1295)

----


### Utils

```js
firebase.utils()
```

#### Android

 - Add `firebase.utils().getPlayServicesStatus(): Promise<GoogleApiAvailabilityType | null>` - [#1257](https://github.com/invertase/react-native-firebase/issues/1257)
  - This is the same as the static `firebase.utils.playServicesAvailability` - but allows forcing an update/refresh of the status

----

### Upgrade instructions

```
npm install --save react-native-firebase@latest
```

> For a reference app to look through versions see our [/tests](https://github.com/invertase/react-native-firebase/tree/master/tests) app.

#### React Native

React Native version `0.56` is now the minimum supported version, it's recommended to upgrade to `0.57.x` if possible, otherwise `0.56` is also acceptable.

#### Android - Update Firebase SDKs

1) In `android/app/build.gradle`, update all the firebase and gms dependencies to the following versions:

- **com.google.android.gms:play-services-base**:{{ android.gms.play-services-base }}
- **com.google.firebase:firebase-core**:{{ android.firebase.core }}
- **com.google.firebase:firebase-ads**:{{ android.firebase.ads }}
- **com.google.firebase:firebase-auth**:{{ android.firebase.auth }}
- **com.google.firebase:firebase-config**:{{ android.firebase.config }}
- **com.google.firebase:firebase-database**:{{ android.firebase.database }}
- **com.google.firebase:firebase-functions**:{{ android.firebase.functions }}
- **com.google.firebase:firebase-invites**:{{ android.firebase.invites }}
- **com.google.firebase:firebase-firestore**:{{ android.firebase.firestore }}
- **com.google.firebase:firebase-messaging**:{{ android.firebase.messaging }}
- **com.google.firebase:firebase-perf**:{{ android.firebase.perf }}
- **com.google.firebase:firebase-storage**:{{ android.firebase.storage }}
- **com.crashlytics.sdk.android:crashlytics**:{{ android.firebase.crashlytics }}

#### iOS - Update Firebase SDKs

v5.0.0 supports iOS SDK versions `5.8.0`, `5.8.1` & `5.9.0` - it's recommended to update to v5.9.0 and set the versions specifically in your `Podfile`:

```ruby
  pod 'Firebase/AdMob', '~> 5.9.0'
  pod 'Firebase/Auth', '~> 5.9.0'
  pod 'Firebase/Core', '~> 5.9.0'
  pod 'Firebase/Database', '~> 5.9.0'
  pod 'Firebase/Functions', '~> 5.9.0'
  pod 'Firebase/DynamicLinks', '~> 5.9.0'
  pod 'Firebase/Firestore', '~> 5.9.0'
  pod 'Firebase/Invites', '~> 5.9.0'
  pod 'Firebase/Messaging', '~> 5.9.0'
  pod 'Firebase/RemoteConfig', '~> 5.9.0'
  pod 'Firebase/Storage', '~> 5.9.0'
  pod 'Firebase/Performance', '~> 5.9.0'
  
  # Crashlytics
  pod 'Fabric', '~> 1.7.11'
  pod 'Crashlytics', '~> 3.10.7'
```

#### Crash Reporting

 - Crash reporting has now removed from the library due to the previous deprecation - if you haven't already; you'll need to remove all usages of it.
 
Crashlytics is the replacement service for crash reporting; see the following links for more information:
 
 - [Firebase - Crashlytics Overview](https://firebase.google.com/docs/crashlytics/)
 - [Crashlytics - React Native - iOS Install Guide](https://rnfirebase.io/docs/v5.x.x/crashlytics/ios)
 - [Crashlytics - React Native - Android Install Guide](https://rnfirebase.io/docs/v5.x.x/crashlytics/android)
 - [Crashlytics - React Native - Reference Docs](https://rnfirebase.io/docs/v5.x.x/crashlytics/reference/crashlytics)

#### Other

 - Remove all usages of `firebase.auth().currentUser.getToken()` - use [ref auth.User#getIdToken] instead
 - Remove  `"AndRetrieveData"` from all auth methods used in `auth()` and `auth().currentUser` methods;
   - e.g. `signInAndRetrieveDataWithEmailAndPassword` becomes `signInWithEmailAndPassword` but still returns a [ref auth.UserCredential] instance as a result
 - Replace all Performance Monitoring `Trace#incrementCounter` calls with [ref perf-mon.Trace#incrementMetric] 
 
----

## Feedback

We want your feedback!

If you have any comments and suggestions or want to report an issue, come find us on [Discord](https://discord.gg/C9aK28N), [Twitter](https://twitter.com/rnfirebase) or [GitHub](https://github.com/invertase/react-native-firebase).

## Contributing

Thank to [all the contributors](https://github.com/invertase/react-native-firebase/graphs/contributors?from=2018-06-28&to=2018-09-26&type=c) that made this release happen 💛. 

If you'd like to contribute please check out our new [testing](https://rnfirebase.io/docs/v5.x.x/testing) and [contributing](https://rnfirebase.io/docs/v5.x.x/contributing) guides.
