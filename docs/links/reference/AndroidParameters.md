# AndroidParameters

Android specific link settings.

## Methods

### setFallbackUrl
[method]setFallbackUrl(fallbackUrl) returns [ref links.DynamicLink];[/method]

Sets the link to open when the app isn't installed. Specify this to do something other than install your app from the Play Store when the app isn't installed, such as open the mobile web version of the content, or display a promotional page for your app.

| Parameter |         |
| --------- | ------- |
| fallbackUrl  | **string** <br /> The link to open on Android if the app is not installed. |

### setMinimumVersion
[method]setMinimumVersion(minimumVersion) returns [ref links.DynamicLink];[/method]

Sets the versionCode of the minimum version of your app that can open the link.

| Parameter |         |
| --------- | ------- |
| minimumVersion  | **number** <br /> The minimum version. |

### setPackageName
[method]setPackageName(packageName) returns [ref links.DynamicLink];[/method]

Sets the Android package name.

| Parameter |         |
| --------- | ------- |
| packageName  | **string** <br /> The package name of the Android app to use to open the link. The app must be connected to your project from the Overview page of the Firebase console. |
