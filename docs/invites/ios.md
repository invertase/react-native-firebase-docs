# iOS Installation

First ensure you have followed the [initial setup guide](version /installation/initial-setup) and the [dynamic links setup guide](version /links/ios).

> On iOS, users must be signed in with their Google Accounts before they can send invitations.

## Add the pod

Add the following to your `Podfile`:

```ruby
pod 'Firebase/Invites'
```

Run `pod update`.

## Update `AppDelegate.m`

Replace the `RNFirebaseLinks` import with `RNFirebaseInvites` at the top of your `ios/[App Name]/AppDelegate.m`:

```objectivec
#import "RNFirebaseInvites.h"
```

Replace the `RNFirebaseLinks` methods with `RNFirebaseInvites` as follows:

```objectivec
- (BOOL)application:(UIApplication *)application
            openURL:(NSURL *)url
            options:(NSDictionary<NSString *, id> *)options {
    return [[RNFirebaseInvites instance] application:application openURL:url options:options];
}

- (BOOL)application:(UIApplication *)application
continueUserActivity:(NSUserActivity *)userActivity
 restorationHandler:(void (^)(NSArray *))restorationHandler {
    return [[RNFirebaseInvites instance] application:application continueUserActivity:userActivity restorationHandler:restorationHandler];
}
```

## Setup Google Sign-In

> Take a look at our [social auth guide](version /auth/social-auth) for how to use Google Sign In with `react-native-firebase`.

Add custom URL schemes to your Xcode project:

    1. Open your project configuration: double-click the project name in the left tree view. Select your app from the TARGETS section, then select the Info tab, and expand the URL Types section.
    
    2. Click the + button, and add a URL scheme for your reversed client ID. To find this value, open the GoogleService-Info.plist configuration file, and look for the REVERSED_CLIENT_ID key. Copy the value of that key, and paste it into the URL Schemes box on the configuration page. Leave the other fields blank.
