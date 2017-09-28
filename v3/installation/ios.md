# iOS Installation

!> Please note that there is a known issue when using Cocoapods with the `use_frameworks!` enabled.  This is explained [here](https://github.com/invertase/react-native-firebase/issues/252#issuecomment-316340974).  Unfortunately we don't currently have a workaround, but are engaging with Firebase directly to try and resolve the problem.

## 1. Setup GoogleService-Info.plist

A `GoogleService-Info.plist` file contains all of the information required by the Firebase iOS SDK to connect to your Firebase project. To automatically generate the plist file, [follow the instructions](https://firebase.google.com/docs/ios/setup#add_firebase_to_your_app) on the Firebase console to "Add Firebase to your app".

Once downloaded, place the file in the root of your iOS app at `ios/[YOUR APP NAME]/GoogleService-Info.plist`.

## 2. Initilize Firebase

> The following instructions are also described on the Firebase console when going through the wizard.

To initilize the native SDK in your app, add the following to your `ios/[YOUR APP NAME]/AppDelegate.m` file:

A) At the top of the file:

```objectivec
#import <Firebase.h>
```

B) Within the `didFinishLaunchingWithOptions:(NSDictionary *)launchOptions` method, before the `return`:

```objectivec
[FIRApp configure];
```

## 3. Setup RNFirebase

TODO

## 4. Install modules

