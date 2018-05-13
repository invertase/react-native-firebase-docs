# Android Installation

## Add the dependency

Add the Firebase Storage dependency to `android/app/build.gradle`:

```groovy
dependencies {
  // ...
  implementation "com.google.firebase:firebase-storage:{{ android.firebase.storage }}"
}
```

## Install the RNFirebase Storage package

Add the `RNFirebaseStoragePackage` to your `android/app/src/main/java/com/[app name]/MainApplication.java`:

```java
// ...
import io.invertase.firebase.RNFirebasePackage;
import io.invertase.firebase.storage.RNFirebaseStoragePackage; // <-- Add this line

public class MainApplication extends Application implements ReactApplication {
    // ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
          new RNFirebasePackage(),
          new RNFirebaseStoragePackage() // <-- Add this line
      );
    }
  };
  // ...
}
```
