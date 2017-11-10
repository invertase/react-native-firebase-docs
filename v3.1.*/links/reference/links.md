# Dynamic Links

[Firebase Dynamic Links](https://firebase.google.com/docs/dynamic-links/) allows you to create and receive links on both Android and iOS platforms.
Assuming the platform specific installation instructions have been followed, Firebase Dynamic Links is ready to go.

React Native Firebase mimics the [Firebase REST API](https://firebase.google.com/docs/dynamic-links/rest) for Dynamic Links creation with a few minor differences:

1. The input for the methods is a javascript object instead of a JSON object.
2. The response contains the URL string only.
3. There is no `dynamicLinkInfo` element. Instead, all of the elements under it were moved into the top-level.

## Methods

The following methods are accessed via the default app's Dynamic Links instance `firebase.links()`.

### createDynamicLink
[method]createDynamicLink(parameters: [LinkConfiguration](#LinkConfiguration)) returns Promise<string>;[/method]

Creates a standard dynamic link.

| Parameter | Type |
| --------- | ------- |
| parameters   | **[LinkConfiguration](#LinkConfiguration)**  |

[collapse Example]
```javascript
firebase.links()
    .createDynamicLink({
      dynamicLinkDomain: "abc123.app.goo.gl",
      link: "https://example.com?param1=foo&param2=bar",
      androidInfo: {
        androidPackageName: "com.example.android"
      },
      iosInfo: {
        iosBundleId: "com.example.ios"
      }
    })
    .then((url) => {
      // ...
    });
```
[/collapse]

### createShortDynamicLink
[method]createShortDynamicLink(parameters: [LinkConfiguration](#LinkConfiguration)) returns Promise<string>;[/method]

Creates a short dynamic link.

| Parameter | Type |
| --------- | ------- |
| parameters   | **[LinkConfiguration](#LinkConfiguration)**  |

[collapse Example]
```javascript
firebase.links()
    .createShortDynamicLink({
      dynamicLinkDomain: "abc123.app.goo.gl",
      link: "https://example.com?param1=foo&param2=bar",
      androidInfo: {
        androidPackageName: "com.example.android"
      },
      iosInfo: {
        iosBundleId: "com.example.ios"
      }
    })
    .then((url) => {
      // ...
    });
```
[/collapse]

### getInitialLink
[method]getInitialLink() returns Promise<string|null>;[/method]

Returns the URL that the app has been launched from. If the app was not launched from a URL the return value will be null.

[collapse Example]
```javascript
firebase.links()
    .getInitialLink()
    .then((url) => {
        if (url) {
            // app opened from a url
        } else {
           // app NOT opened from a url
        }
    });
```
[/collapse]

### onLink
[method]onLink(listener: Function<string>) returns Function;[/method]

Subscribe to URL open events while the app is still running.

The listener is called from URL open events whilst the app is still running, use [getInitialLink](#getInitialLink) for URLs which cause the app to open from a previously closed / not running state.

Returns an unsubscribe function, call the returned function to unsubscribe from all future events.

[collapse Example]
```javascript
// subscribe
const unsubscribe = firebase.links().onLink((url) => {
  // ...
});

// unsubscribe
unsubscribe();
```
[/collapse]


## Types

### LinkConfiguration

For more information about each parameter below see the parameters section of the official Firebase docs [here.](https://firebase.google.com/docs/reference/dynamic-links/link-shortener)

[collapse Definition]
```typescript
{
  link: 'string',
  dynamicLinkDomain: 'string',
  androidInfo?: {
    androidLink?: 'string',
    androidPackageName: 'string',
    androidFallbackLink?: 'string',
    androidMinPackageVersionCode?: 'string',
  },
  iosInfo?: {
    iosBundleId: 'string',
    iosAppStoreId?: 'string',
    iosFallbackLink?: 'string',
    iosCustomScheme?: 'string',
    iosIpadBundleId?: 'string',
    iosIpadFallbackLink?: 'string',
  },
  socialMetaTagInfo?: {
    socialTitle: 'string',
    socialImageLink: 'string',
    socialDescription: 'string',
  },
  suffix?: {
    option: 'string',
  },
}
```
[/collapse]
