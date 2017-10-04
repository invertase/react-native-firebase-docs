# FirebaseApp

## Methods

### extendApp
[method]extendApp(props) returns void;[/method]

Allows adding additional properties onto a firebase app instance.

?> This methods is undocumented on the web SDK.

| Parameter |         |
| --------- | ------- |
| props   | **Object**  |

### onReady
[method]onReady() returns Promise containing [FirebaseApp](#methods);[/method]

Resolves a promise once the FirebaseApp instance has been initilized.

## Properties

### name
[method]name returns string;[/method]

### options
[method]options returns Object;[/method]

## Unsupported Methods

### delete

FirebaseApp.delete is only supported on iOS, therefore we cannot support it. Please see [this issue comment](https://github.com/firebase/firebase-ios-sdk/issues/140#issuecomment-315953708) for more information.
