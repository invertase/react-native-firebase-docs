# Admob

```
firebase.admob
```

## Methods 

The following methods are accessed via the Admob instance `firebase.admob()`.

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
[method]interstitial(unitId) returns [Interstitial](version /admob/interstitial);[/method]

Returns a new [Interstitial](version /admob/interstitial) to be loaded with a given unitId.

| Parameter |         |
| --------- | ------- |
| unitId   | **string** <br /> Ad unitId |

### rewarded
[method]rewarded(unitId) returns [RewardedVideo](version /admob/rewarded-video);[/method]

Returns a new [RewardedVideo](version /admob/rewarded-video) to be loaded with a given unitId.

| Parameter |         |
| --------- | ------- |
| unitId   | **string** <br /> Ad unitId |

## Statics

### Banner
[method]Banner returns [Banner](version /admob/banner);[/method]

Returns a [Banner](version /admob/banner) component.

### NativeExpress
[method]NativeExpress returns [NativeExpress](version /admob/native-express);[/method]

Returns a [NativeExpress](version /admob/native-express) component.

### AdRequest
[method]AdRequest returns [AdRequest](version /admob/ad-request);[/method]

Returns a [AdRequest](version /admob/ad-request) class.

### VideoOptions
[method]VideoOptions returns [VideoOptions](version /admob/video-options);[/method]

Returns a [VideoOptions](version /admob/video-options) class.

## Types

### EventTypes
[method]VideoOptions returns [EventTypes](https://github.com/invertase/react-native-firebase/blob/master/lib/modules/admob/EventTypes.js#L2);[/method]

Returns an `Object` containing Admob event types.

### RewardedVideoEventTypes
[method]RewardedVideoEventTypes returns [RewardedVideoEventTypes](https://github.com/invertase/react-native-firebase/blob/master/lib/modules/admob/EventTypes.js#L10);[/method]

Returns an `Object` containing [RewardedVideo](#rewarded) event types.

### NativeExpressEventTypes
[method]NativeExpressEventTypes returns [NativeExpressEventTypes](https://github.com/invertase/react-native-firebase/blob/master/lib/modules/admob/EventTypes.js#L18);[/method]

Returns an `Object` containing [NativeExpress](#nativeexpress) event types.
