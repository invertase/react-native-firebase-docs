# Android Troubleshooting

## Duplicate Dex Files error (build time error)

A common build time error when using libraries that require google play services is of the form:
`Failed on android with com.android.dex.DexException: Multiple dex files...`

This error (https://github.com/invertase/react-native-firebase/issues/48) occurs because different versions of google play services or google play services modules are being required by different libraries.

The process to fix this is fairly manual and depends on your specific combination of external libraries. Essentially what's required is to check the app level build.gradle file of each external library and establish which ones have a Google Play Services dependency.

You then need to find the lowest common version of each G.P.S module dependency, require that in the app level build.gradle file of your own project, and exclude it from being required by the modules themselves. This will force the use of a consistent version of the G.P.S module.

It's not a good idea to modify the version within the library's build.gradle, as this will be overwritten when you update the library, which will lead to the build breaking again.

A good break down of this process can be found here:
https://medium.com/@suchydan/how-to-solve-google-play-services-version-collision-in-gradle-dependencies-ef086ae5c75f

## Missing Byte Code (build time error)

When running your app from within Android Studio, you may encounter `Missing Byte Code` errors.  This is due to a known issue with version 3.1.x of the android tools plugin: https://issuetracker.google.com/issues/72811718.  You'll need to disable Instant Run to get past this error.

## NoSuchMethodError: No virtual method (run time error)

A common run time error when using `react-native-firebase` is of the form:
`java.lang.NoSuchMethodError: No virtual method...`

This error occurs if you're compiling against an old version of the Google Play Services libraries.

To fix, update the Google Play Services dependencies in your `android/app/build.gradle` to a later version - we recommend making sure you're using the latest version of all Google Play Services dependencies.

## NoSuchMethodError: No static method (run time error)

Another common run time error when using `react-native-firebase` is of the form:
`java.lang.NoSuchMethodError: No static method...`

This error can occur if you have a mismatch of versions in your Google Play Services dependencies.  This can often happen if you have multiple third party libraries that import Google Play Services dependencies.

To fix, follow the instructions above for how to fix Duplicate Dex Files error

## Google Play Services related issues

The firebase SDK requires a certain version of Google Play Services installed on Android in order to function properly.

If the version of Google Play Services installed on your device is incorrect or non existent, React Native Firebase will throw a red box error, and your app will possibly crash as well. The red box error will have a numerical code associated with it. These codes can be found here:

 https://developers.google.com/android/reference/com/google/android/gms/common/ConnectionResult#SERVICE_VERSION_UPDATE_REQUIRED

Here is a quick guide to some of the most common errors encountered:

code 2 -  Google Play Services is required to run this application but no valid installation was found:

The emulator/device you're using does not have the Play Services SDK installed.

- Emulator: Open SDK manager, under 'SDK Tools' ensure "Google Play services, rev X" is installed. Once installed,
create a new emulator image. When selecting your system image, ensure the target comes "with Google APIs".
- Device: Play Services needs to be downloaded from the Google Play Store.

code 9 - The version of the Google Play services installed on this device is not authentic:

This error applies to modified or 'shimmed' versions of Google Play Services which you might be using in a third
party emulator such as GenyMotion.

Using this kind of workaround with Google Play Services can be problematic, so we
recommend using the native Android Studio emulators to reduce the chance of these complications.

## Turning off Google Play Services availability errors

Google Play Services errors can be turned off using a config option like so:

```javascript
firebase.utils().errorOnMissingPlayServices = false;
firebase.utils().promptOnMissingPlayServices = false;
```

This must be called at the module scope, outside any classes, preferably before any other usages of `react-native-firebase` so that it's disabled before the internal logic takes over.

## Checking for Google Play Services availability with React Native Firebase

React Native Firebase actually has a useful helper object for checking Google Play Services availability.  The following examples show how to use this helper:

### Basic Google Play Services check

Call this function in your startup logic, before `react-native-firebase` usage.

This example does pretty much what promptOnMissingPlayServices = true does.

```javascript
async function checkPlayServicesBasicExample() {
  const utils = firebase.utils();

  const {
    isAvailable,
    hasResolution,
    isUserResolvableError,
  } = utils.playServicesAvailability;

  // all good and valid \o/
  if (isAvailable) return Promise.resolve();

  // if the user can resolve the issue i.e by updating play services
  // then call Google Play's own/default prompting functionality
  if (isUserResolvableError) {
    return utils.promptForPlayServices();
  }

  // call Google Play's own/default resolution functionality
  if (hasResolution) {
    return utils.resolutionForPlayServices();
  }

  // There's no way to resolve play services on this device
  // probably best to show a dialog / force crash the app
  return Promise.reject(
    new Error('Unable to find a valid play services version.')
  );
}
```

### Advanced Google Play Service check

Call this function in your startup logic, before `react-native-firebase` usage.

This example shows usage of status codes to allow custom dialogs/user feedback.

```javascript
async function checkPlayServicesAdvancedExample() {
  const utils = firebase.utils();

  const {
    status,
    isAvailable,
    hasResolution,
    isUserResolvableError,
  } = utils.playServicesAvailability;

  // all good and valid \o/
  if (isAvailable) return Promise.resolve();

  // if the user can resolve the issue i.e by updating play services
  // then call Google Play's own/default prompting functionality
  if (isUserResolvableError || hasResolution) {
    switch (status) {
      case 1:
        // SERVICE_MISSING - Google Play services is missing on this device.
        // show something to user
        // and then attempt to install if necessary
        return utils.makePlayServicesAvailable();
      case 2:
        // SERVICE_VERSION_UPDATE_REQUIRED - The installed version of Google Play services is out of date.
        // show something to user
        // and then attempt to update if necessary
        return utils.resolutionForPlayServices();
      // TODO handle other cases as necessary, see link below for all codes and descriptions
      // TODO e.g. https://developers.google.com/android/reference/com/google/android/gms/common/ConnectionResult#SERVICE_VERSION_UPDATE_REQUIRED
      default:
        // some default dialog / component?
        if (isUserResolvableError) return utils.promptForPlayServices();
        if (hasResolution) return utils.resolutionForPlayServices();
    }
  }

  // There's no way to resolve play services on this device
  // probably best to show a dialog / force crash the app
  return Promise.reject(
    new Error('Unable to find a valid play services version.')
  );
}
```
