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


[collapse RNFirebase Client SDK Example]
```js
const httpsCallable = firebase.functions().httpsCallable('myFooBarFn');

httpsCallable({ some: 'args' })
    .then(({ data }) => {
        console.log(data.someResponse);
    })
    .catch(httpsError => {
        console.log(httpsError.code);
        console.log(httpsError.message);
        console.log(httpsError.details.foo);
    })
```
[/collapse]

[collapse Firebase Cloud Function Example]
```js
const functions = require('firebase-functions');

exports.myFooBarFn = functions.https.onCall(data => {
    console.log(data.some);

    if (!data.some) {
        throw new functions.https.HttpsError(
          'invalid-argument', // code
          'Your error message goes here', // message
          { foo: 'bar' }, // details - optional and can be anything JSON serializable
        );
    }

    return { someResponse: 'hello world' };
});
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

[method] type HttpsCallablePromise = Promise<HttpsCallableResult>| Promise<[ref functions.HttpsError]>; [/method]


----

## Links

 - [Official Firebase Functions Documentation](https://firebase.google.com/docs/functions/callable)
 - [RNFirebase - Functions Test Suite](https://github.com/invertase/react-native-firebase/blob/master/bridge/e2e/functions/functions.e2e.js)
 - [RNFirebase - Test Cloud Function](https://github.com/invertase/react-native-firebase/tree/master/bridge/functions)