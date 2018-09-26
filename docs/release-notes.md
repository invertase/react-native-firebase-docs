# Release Notes

## v5.0.0

TODO / WIP

----

### Quick Start

Install using:
 
```
npm install --save react-native-firebase@latest
```

### General

----

### Messaging 

----

### Firebase Invites

----

### Dynamic Links


----

### Cloud Firestore


----

### Authentication


----

### Database


----

### Crashlytics



----

### Upgrade instructions

```
npm install --save react-native-firebase@latest
```

> For a reference app to look through versions see our [/tests](https://github.com/invertase/react-native-firebase/tree/master/tests) app.

#### React Native

React Native version `0.56` is now the minimum supported version, it's recommended to upgrade to `0.57.x` if possible.

#### Android - Firebase SDK Versions

1) In `android/app/build.gradle`, update all the firebase and gms dependencies to the following versions:

- **com.google.android.gms:play-services-base**: {{ android.gms.play-services-base }}
- **com.google.firebase:firebase-core**: {{ android.firebase.core }}
- **com.google.firebase:firebase-ads**: {{ android.firebase.ads }}
- **com.google.firebase:firebase-auth**: {{ android.firebase.auth }}
- **com.google.firebase:firebase-config**: {{ android.firebase.config }}
- **com.google.firebase:firebase-database**: {{ android.firebase.database }}
- **com.google.firebase:firebase-functions**: {{ android.firebase.functions }}
- **com.google.firebase:firebase-invites**: {{ android.firebase.invites }}
- **com.google.firebase:firebase-firestore**: {{ android.firebase.firestore }}
- **com.google.firebase:firebase-messaging**: {{ android.firebase.messaging }}
- **com.google.firebase:firebase-perf**: {{ android.firebase.perf }}
- **com.google.firebase:firebase-storage**: {{ android.firebase.storage }}
- **com.crashlytics.sdk.android:crashlytics**:  {{ android.firebase.crashlytics }}

#### iOS - Firebase SDK Versions

v5.0.0 supports iOS SDK versions 5.8.0, 5.8.1 & 5.9.0 - it's recommended to update to v5.9.0:

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

- Crash reporting is now removed from the library due to the previous deprecation - if you haven't already; you'll need to remove all usages of it.

----

## Feedback

We want your feedback!

If you have any comments and suggestions or want to report an issue, come find us on [Discord](https://discord.gg/C9aK28N)


## Contributing

