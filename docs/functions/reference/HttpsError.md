# HttpsError

```ts
type HttpsError implements Error {
  +details: ?any;
  +code: FunctionsErrorCode;
}
```

----

## Properties

### code
[method]code returns [FunctionsErrorCode](#Types);[/method]

A standard error code as returned by the first arg of your thrown error on cloud functions.

[collapse Cloud Function Example]
```js
// inside your cloud function
throw new functions.https.HttpsError(
  'cancelled', // <---- THIS
  'Your error message goes here.',
  { foo: 'bar' },
);
```
[/collapse]


----

### message
[method]message returns string;[/method]

Your error message as thrown in your cloud function.

[collapse Cloud Function Example]
```js
// inside your cloud function
throw new functions.https.HttpsError(
  'cancelled',
  'Your error message goes here.', // <---- THIS
  { foo: 'bar' },
);
```
[/collapse]

----

### details
[method]details returns ?any;[/method]

Extra data thrown with your error on your cloud function.

[collapse Cloud Function Example]
```js
// inside your cloud function
throw new functions.https.HttpsError(
  'cancelled',
  'Your error message goes here.',
  { foo: 'bar' }, // <---- THIS
);
```
[/collapse]


----

## Types

### FunctionsErrorCode

Statics for these also exist for equality comparisons e.g. `firebase.functions.HttpsErrorCode.CANCELLED` outputs `cancelled`;

```ts
type FunctionsErrorCode =
  | 'ok'
  | 'cancelled'
  | 'unknown'
  | 'invalid-argument'
  | 'deadline-exceeded'
  | 'not-found'
  | 'already-exists'
  | 'permission-denied'
  | 'resource-exhausted'
  | 'failed-precondition'
  | 'aborted'
  | 'out-of-range'
  | 'unimplemented'
  | 'internal'
  | 'unavailable'
  | 'data-loss'
  | 'unauthenticated';
```