# Android Installation

First ensure you have followed the [initial setup guide](version /installation/initial-setup) and the [dynamic links setup guide](version /links/android).

Secondly ensure you have SHA fingerprint added in your Firebase console, under the 'General settings' tab. Otherwise you will a 'Message failed to send' error.

## Install the RNFirebase Invites package

Add the `RNFirebaseInvitesPackage` to your `android/app/src/main/java/com/[app name]/MainApplication.java`:

```java
// ...
import io.invertase.firebase.RNFirebasePackage;
import io.invertase.firebase.invites.RNFirebaseInvitesPackage; // <-- Add this line

public class MainApplication extends Application implements ReactApplication {
    // ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
          new RNFirebasePackage(),
          new RNFirebaseInvitesPackage() // <-- Add this line
      );
    }
  };
  // ...
}
```
