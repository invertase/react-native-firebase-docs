# Getting Started

React Native Firebase (RNFirebase) is a well tested feature rich library which enables you to use the native Firebase iOS & Android SDKs in your React Native environment through an intuitive JavaScript API, which matches the Firebase web SDK where possible. 
 
To get started, [follow our installation guide](version installation/initial-setup).

## RNFirebase vs Firebase web SDK

Although the Firebase Web SDK library will work with React Native, it is mainly built for the web.

RNFirebase provides a JavaScript bridge to the native Firebase SDKs for both iOS and Android therefore Firebase will run on the native thread, allowing the rest of your app to run on the JS thread. The Firebase Web SDK also runs on the JS thread, therefore potentially affecting the frame rate causing jank with animations, touch events etc.

The native SDKs also allow us to hook into device sdk's which are not possible with the web SDK, for example crash reporting, offline realtime database support, analytics and more!

All in all, RNFirebase provides much faster performance over the web SDK and provides device sdk's not found in the web sdk (see the feature table below).

## Supported Firebase Modules

> The Web SDK column indicates what modules/functionality from the Web SDK are usable within React Native. A `?` indicates partial support.

| Firebase Features      | v1.x.x  | v2.x.x  | v3.x.x | Web SDK |
| ---------------------- | :---: | :---: | :---: | :---: |
| **AdMob**                  | ❌ | ✅ | ✅ | ❌ |
| **Analytics**              | ✅ | ✅ | ✅ | ❌ |
| **App Indexing**           | ❌ | ❌ | ❌ | ❌ |
| **Authentication**         | ✅ | ✅ | ✅ | ✅ |
| _-- Phone Auth_            | ❌ | ❌ | ✅ | ❌ |
| **Core**                   | ❌ |**?**| ✅ | ✅ |
|  _-- Multiple Apps_        | ❌ | ❌ | ✅ | ✅ |
| **Cloud Messaging (FCM)**  | ✅ | ✅ | ✅ |**?**|
| **Crash Reporting**        | ✅ | ✅ | ✅ | ❌ |
| **Dynamic Links**          | ❌ | ❌ | ❌ | ❌ |
| **Invites**                | ❌ | ❌ | ❌ | ❌ |
| **Performance Monitoring** | ✅ | ✅ | ✅ | ❌ |
| **Realtime Database**      | ✅ | ✅ | ✅ | ✅ |
| _-- Offline Persistence_   | ✅ | ✅ | ✅ |**?**|
| _-- Transactions_          | ✅ | ✅ | ✅ | ✅ |
| **Remote Config**          | ✅ | ✅ | ✅ | ❌ |
| **Storage**                | ✅ | ✅ | ✅ |**?**|

### Supported versions

> The table below shows the supported version of `react-native-firebase` for different React Native versions

|                                 | v0.36 - v0.39  | v0.40 - v0.46  | v0.47 +
| ------------------------------- | :---: | :---: | :---: |
| react-native-firebase           | 1.X.X | 2.X.X | 2.1.X |

> The table below shows the minimum supported versions of the Firebase SDKs for each version of `react-native-firebase`

|                        | v1  | v2  | v3  |
| ---------------------- | :---: | :---: | :---: |
| Firebase Android SDK   | 10.2.0+ | 11.0.0 + | 11.2.0 + |
| Firebase iOS SDK       | 3.15.0+ | 4.0.0 +  | 4.0.0 +  |
