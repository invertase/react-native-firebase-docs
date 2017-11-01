# Remote Config

```
firebase.config
```

## Methods

The following methods are accessed via the Config instance `firebase.config()`.

### enableDeveloperMode
[method]enableDeveloperMode() returns void;[/method]

Enable Remote Config developer mode to allow for frequent refreshes of the cache.

### setDefaults
[method]setDefaults(defaults) returns void;[/method]

Sets default values for the app to use when accessing values. Any data fetched and activated will override any default values. Any values in the defaults but not on Firebase will be untouched.

| Parameter |         |
| --------- | ------- |
| defaults   | **object**  |

### fetch
[method]fetch(duration) returns Promise<void>;[/method]

Fetches the remote config data from Firebase, defined in the dashboard. If duration is defined (seconds), data will be locally cached for this duration.

The default duration is 43200 seconds (12 hours). To force a cache refresh call the method with a duration of 0.

| Parameter |         |
| --------- | ------- |
| duration   | **number** <br /> Duration in seconds to cache the data for |

Thrown errors can be one of the following:

| code | message        |
| --------- | ------- |
| config/failure   | Config fetch failed |
| config/no_fetch_yet   | Config has never been fetched |
| config/throttled   | Config fetch was throttled |

### activateFetched
[method]activateFetched() returns Promise containing boolean;[/method]

Moves fetched data in the apps active config. Always successfully resolves with a boolean value of whether the fetched config was moved successfully.

### getValue
[method]getValue(key) returns Promise containing snapshot;[/method]

Gets a config item by key. Returns a snapshot containing source (`default`, `remote` or `static`) and `val` function.

| Parameter |         |
| --------- | ------- |
| key   | **string** |

### getValues
[method]getValue(keys) returns Promise containing object of snapshots;[/method]

Gets multiple values by key. Returns an snapshot object of keys with the same object returned from [ref config#getValue], e.g. `snapshots.foo.val()`.

| Parameter |         |
| --------- | ------- |
| keys   | **Array<string>** |

### getKeysByPrefix
[method]getKeysByPrefix(prefix) returns Promise containing array of strings;[/method]

Returns all keys as an array by a prefix. If no prefix is defined all keys are returned.

| Parameter |         |
| --------- | ------- |
| prefix    | **string** (optional) |

### setDefaultsFromResource
[method]setDefaultsFromResource(filename) returns void;[/method]

Sets the default values from a resource:

- Android: Id for the XML resource, which should be in your application's res/xml folder.
- iOS: The plist file name, with no file name extension.

| Parameter |         |
| --------- | ------- |
| filename  | **string** or **number** |
