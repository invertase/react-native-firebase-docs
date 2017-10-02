# Admob

```
firebase.admob
```

## Methods 

### initialize
[method]initialize(id) returns void;[/method]

Before using any AdMob feature, ensure you call the initialize method. This only needs to be done once per the apps lifecycle. Initialize takes your AdMob App ID, where you can find on your AdMob dashboard.

For testing purposes, you can use the Admob test app ID "ca-app-pub-3940256099942544~3347511713"

| Parameter |         |
| --------- | ------- |
| id   | **string**  |

### openDebugMenu
[method]openDebugMenu() returns void;[/method]

Opens a debug menu, allowing you to test your ads. This menu cannot be closed unless you reload your app.

### interstitial
[method]interstitial(unitId) returns $[Intersistaial](/admob/interstitial);[/method]

Returns a new Intersistaial to be loaded with a given unitId.

| Parameter |         |
| --------- | ------- |
| unitId   | **string** <br /> Ad unitId |

### rewarded
[method]rewarded(unitId) returns ...;[/method]

Returns a new Rewarded Video to be loaded with a given unitId.

| Parameter |         |
| --------- | ------- |
| unitId   | **string** <br /> Ad unitId |

## Statics

### Banner
[method]Banner returns ...;[/method]

Returns a [Banner](#) component.

### NativeExpress
[method]NativeExpress returns ...;[/method]

Returns a [NativeExpress](#) component.

### AdRequest
[method]AdRequest returns ...;[/method]

Returns a [AdRequest](#) class.

### VideoOptions
[method]VideoOptions returns ...;[/method]

Returns a [VideoOptions](#) class.

## Types

### EventTypes
[method]VideoOptions returns [EventTypes](https://github.com/invertase/react-native-firebase/blob/master/lib/modules/admob/EventTypes.js#L2);[/method]

Returns an `Object` containing Admob event types.

### RewardedVideoEventTypes
[method]RewardedVideoEventTypes returns [RewardedVideoEventTypes](https://github.com/invertase/react-native-firebase/blob/master/lib/modules/admob/EventTypes.js#L10);[/method]

Returns an `Object` containing [RewardedVideo](#rewardedvideo) event types.

### NativeExpressEventTypes
[method]NativeExpressEventTypes returns [NativeExpressEventTypes](https://github.com/invertase/react-native-firebase/blob/master/lib/modules/admob/EventTypes.js#L18);[/method]

Returns an `Object` containing [NativeExpress](#nativeexpress) event types.
