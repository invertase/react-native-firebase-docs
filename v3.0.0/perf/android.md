# Android Installation

## Add the dependency

Add the Firebase Performance Monitoring dependancy to `android/app/build.gradle`:

```
dependencies {
  ...
  compile "com.google.firebase:firebase-perf:{{ android.firebase.version }}"
}
```

## Install the RNFirebase Performance package

Add the `RNFirebasePerformancePackage` to your `android/app/src/main/java/com/[app name]/MainApplication.java`:

```java
...
import io.invertase.firebase.RNFirebasePackage;
import io.invertase.firebase.perf.RNFirebasePerformancePackage; // <-- Add this line

public class MainApplication extends Application implements ReactApplication {
    // ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
          new RNFirebasePackage(),
          new RNFirebasePerformancePackage() // <-- Add this line
      );
    }
  };
  // ...
}
```
