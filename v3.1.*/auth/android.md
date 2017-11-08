# Android Installation

## Add the dependency

Add the Firebase Authentication dependancy to `android/app/build.gradle`:

```groovy
dependencies {
  // ...
  compile "com.google.firebase:firebase-auth:{{ android.firebase.version }}"
}
```

## Install the RNFirebase Authentication package

Add the `RNFirebaseAuthPackage` to your `android/app/src/main/java/com/[app name]/MainApplication.java`:

```java
// ...
import io.invertase.firebase.RNFirebasePackage;
import io.invertase.firebase.auth.RNFirebaseAuthPackage; // <-- Add this line

public class MainApplication extends Application implements ReactApplication {
    // ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
          new RNFirebasePackage(),
          new RNFirebaseAuthPackage() // <-- Add this line
      );
    }
  };
  // ...
}
```
