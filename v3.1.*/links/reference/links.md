# Dynamic Links

[Firebase Dynamic Links](https://firebase.google.com/docs/dynamic-links/) allows you to create and receive links on both Android and iOS platforms.
Assuming the installation instructions have been followed, Firebase Dynamic Links is ready to go.

```
firebase.links()
```

## Create Dynamic Links

React Native Firebase mimics the [Firebase REST API](https://firebase.google.com/docs/dynamic-links/rest) for Dynamic Links creation.

The differences from the REST API are:
1. The input for the methods is a javascript object instead of a JSON object.
2. The response contains the URL string only.
3. There is no `dynamicLinkInfo` element. Instead, all of the elements under it were moved into the top-level.


## Methods

The following methods are accessed via the default app's Dynamic Links instance `firebase.links()`.

### createDynamicLink
[method]createDynamicLink(parameters) returns Promise<String>;[/method]

Creates a standard dynamic link.

| Parameter |         |
| --------- | ------- |
| parameters   | **object**  |

[collapse Example]
```javascript
firebase.links().createDynamicLink({
  dynamicLinkDomain: "abc123.app.goo.gl",
  link: "https://example.com?param1=foo&param2=bar",
  androidInfo: {
    androidPackageName: "com.example.android"
  },
  iosInfo: {
    iosBundleId: "com.example.ios"
  }
}).
then((url) => {
  // ...
});
```
[/collapse]
