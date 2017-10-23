## Default Firebase App

!> Calling `initializeApp()` for the default app will throw an 'app already initialized' error as it is already initialized natively.

After following the iOS & Android install guides and correctly setting up your google services plist/json files; the default app is automatically initialized and available for use in react-native-firebase.

There's no need to call `initializeApp(options)` in your JS code for the default app, import RNFirebase and use the default app straight away:

```javascript
import firebase from 'react-native-firebase';

console.log(firebase.database().app.name); // '[DEFAULT]'
```

## Enable Database Persistence

Enabling database persistence for the default app is not supported via the JS api. This is to prevent several race condition issues with accessing `database()` over the RN Bridge before calling persistence.

You can still however easily enable this natively for the default app instance:

### Android

Add the below line inside your `MainActivity.java` file `onCreate()` method:

```java
FirebaseDatabase.getInstance().setPersistenceEnabled(true);
```

### iOS

Add the below line after the `[FIRApp configure];` line inside your `AppDelegate.m` file `didFinishLaunchingWithOptions` method:

```objectivec
[FIRDatabase database].persistenceEnabled = YES;
```
