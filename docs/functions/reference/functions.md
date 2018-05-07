# Functions

```
firebase.functions
```

## Methods

The following methods are accessed via the Functions instance `firebase.functions()`.

### httpsCallable
[method]httpsCallable(name: string) returns (data?: any): [HttpsCallablePromise](#Types) => {};[/method]

Gets an `HttpsCallable` instance that refers to the function with the given name.

| Parameter |         |
| --------- | ------- |
| name      | **string** <br /> The name of the https callable function. |


[collapse Example]
```js
const httpsCallable = firebase.functions().httpsCallable('myFooBarFn');
```
[/collapse]


## Types

### HttpsCallableResult

```ts
type HttpsCallableResult = {
  data: Object,
};
```

### HttpsCallablePromise

```ts
type HttpsCallablePromise = Promise<HttpsCallableResult>| Promise<HttpsError>;
```

## Links

 - [Official Firebase Functions Documentation](https://firebase.google.com/docs/functions/callable)
 - [RNFirebase - Functions Test Suite](https://github.com/invertase/react-native-firebase/blob/master/bridge/e2e/functions/functions.e2e.js)
 - [RNFirebase - Test Cloud Function](https://github.com/invertase/react-native-firebase/tree/master/bridge/functions)