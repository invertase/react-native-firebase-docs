# Android Installation

## Add the dependency

Add the Firebase Remote Config dependancy to `android/app/build.gradle`:

```
dependencies {
  ...
  compile "com.google.firebase:firebase-config:{{ android.firebase.version }}"
}
```

## Install the RNFirebase Remote Config package

Add the `RNFirebaseRemoteConfigPackage` to your `android/app/src/main/java/com/[app name]/MainApplication.java`:

```java
...
import io.invertase.firebase.RNFirebasePackage;
import io.invertase.firebase.config.RNFirebaseRemoteConfigPackage; // <-- Add this line

public class MainApplication extends Application implements ReactApplication {
    // ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
          new RNFirebasePackage(),
          new RNFirebaseRemoteConfigPackage() // <-- Add this line
      );
    }
  };
  // ...
}
```
