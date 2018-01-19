# Android Installation

## Add the dependency

Add the Firebase Realtime Database dependency to `android/app/build.gradle`:

```groovy
dependencies {
  // ...
  compile "com.google.firebase:firebase-database:{{ android.firebase.version }}"
}
```

## Install the RNFirebase Database package

Add the `RNFirebaseDatabasePackage` to your `android/app/src/main/java/com/[app name]/MainApplication.java`:

```java
// ...
import io.invertase.firebase.RNFirebasePackage;
import io.invertase.firebase.database.RNFirebaseDatabasePackage; // <-- Add this line

public class MainApplication extends Application implements ReactApplication {
    // ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
          new RNFirebasePackage(),
          new RNFirebaseDatabasePackage() // <-- Add this line
      );
    }
  };
  // ...
}
```
