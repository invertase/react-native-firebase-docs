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
[method]createDynamicLink(parameters: [LinkConfiguration](#LinkConfiguration) returns Promise<String>;[/method]

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
[method]createShortDynamicLink(parameters: [LinkConfiguration](#LinkConfiguration) returns Promise<String>;[/method]

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

## Types

### LinkConfiguration

For more information [see reference](https://firebase.google.com/docs/reference/dynamic-links/link-shortener)

[collapse Type Definitiion]
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
