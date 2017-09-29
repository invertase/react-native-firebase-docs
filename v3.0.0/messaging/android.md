# Android Installation

## Add the dependency

Add the Firebase Cloud Messaging dependancy to `android/app/build.gradle`:

```
dependencies {
  ...
  compile "com.google.firebase:firebase-messaging:{{ android.firebase.version }}"
}
```

## Install the RNFirebase Messaging package

Add the `RNFirebaseMessagingPackage` to your `android/app/src/main/java/com/[app name]/MainApplication.java`:

```java
...
import io.invertase.firebase.RNFirebasePackage;
import io.invertase.firebase.messaging.RNFirebaseMessagingPackage; // <-- Add this line

public class MainApplication extends Application implements ReactApplication {
    // ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
          new RNFirebasePackage(),
          new RNFirebaseMessagingPackage() // <-- Add this line
      );
    }
  };
  // ...
}
```
