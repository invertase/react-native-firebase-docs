# Android Installation

## 1. Setup google-services.json

A google-services.json file contains all of the information required by the Firebase Android SDK to connect to your Firebase project. To automatically generate the json file, [follow the instructions](https://firebase.google.com/docs/android/setup#add_firebase_to_your_app) on the Firebase console to "Add Firebase to your app".

Once downloaded, place this file in the root of your project at `android/app/google-services.json`.

> The following instructions are also described on the Firebase console when going through the wizard.

In order for Android to parse this file, add the google-services gradle plugin as a dependency to your project in the *project* level `build.gradle` file:

```java
buildscript {
  // ...
  dependencies {
    // ...
    classpath 'com.google.gms:google-services:{{ android.google.services }}'
  }
}
```

To apply the plugin to your project, add the following to the **VERY BOTTOM** of your app `android/app/build.gradle` file:

```java
apply plugin: 'com.google.gms.google-services'
```

## 2. Link RNFirebase

RNFirebase now needs to be linked into your Android project.

### Add the project path

Within your `android/settings.gradle`, add the following:

```groovy
include ':react-native-firebase'
project(':react-native-firebase').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-firebase/android')
```

### Add RNFirebase & Firebase modules

Both the RNFirebase module and the Firebase modules need to be installed as project dependencies. In the `android/app/build.gradle` file, add the following:

```groovy
dependencies {
  // RNFirebase dependency
  compile(project(':react-native-firebase')) {
    transitive = false
  }
  
  // Firebase dependancies
  compile "com.google.android.gms:play-services-base:{{ android.firebase.version }}"
  compile "com.google.firebase:firebase-core:{{ android.firebase.version }}"
  
  ...
```

### Add RNFirebase as a React Native module

To install `react-native-firebase` in your project, you'll need to import the packages you need from `io.invertase.firebase` in your project's `android/app/src/main/java/com/[app name]/MainApplication.java` and list them as packages for ReactNative in the `getPackages()` function:

```java
package com.youcompany.application;
...

import io.invertase.firebase.RNFirebasePackage; // <-- Add this line

public class MainApplication extends Application implements ReactApplication {
    // ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
          new RNFirebasePackage()  // <-- Add this line
      );
    }
  };

}
```

### Install modules

The `RNFirebasePackage` only provides your application with access to [Core](version /core/reference) features. Check out the installation guides on the other modules for how to use other Firebase features.
