# HttpsError

```ts
type HttpsError implements Error
```

## Properties

### code
[method]code returns [FunctionsErrorCode](#types);[/method]

A standard error code as returned by the first arg of your thrown error on cloud functions.

```js
// inside your cloud function
throw new functions.https.HttpsError(
  'cancelled', // <---- THIS
  'Your error message goes here.',
  { foo: 'bar' },
);
```

#### Possible values

These values can also be access via statics, e.g. `firebase.functions.HttpsErrorCode.CANCELLED`;

- `cancelled`: The operation was cancelled (typically by the caller).
- `unknown`: Unknown error or an error from a different error domain.
- `invalid-argument`: Client specified an invalid argument. Note that this
  differs from `failed-precondition`. `invalid-argument` indicates
  arguments that are problematic regardless of the state of the system
  (e.g. an invalid field name).
- `deadline-exceeded`: Deadline expired before operation could complete.
  For operations that change the state of the system, this error may be
  returned even if the operation has completed successfully. For example,
  a successful response from a server could have been delayed long enough
  for the deadline to expire.
- `not-found`: Some requested document was not found.
- `already-exists`: Some document that we attempted to create already
  exists.
- `permission-denied`: The caller does not have permission to execute the
  specified operation.
- `resource-exhausted`: Some resource has been exhausted, perhaps a
  per-user quota, or perhaps the entire file system is out of space.
- `failed-precondition`: Operation was rejected because the system is not
  in a state required for the operation's execution.
- `aborted`: The operation was aborted, typically due to a concurrency
  issue like transaction aborts, etc.
- `out-of-range`: Operation was attempted past the valid range.
- `unimplemented`: Operation is not implemented or not supported/enabled.
- `internal`: Internal errors. Means some invariants expected by
  underlying system has been broken. If you see one of these errors,
  something is very broken.
- `unavailable`: The service is currently unavailable. This is most likely
  a transient condition and may be corrected by retrying with a backoff.
- `data-loss`: Unrecoverable data loss or corruption.
- 'unauthenticated': The request does not have valid authentication
  credentials for the operation.

### message
[method]message returns string;[/method]

Your error message as thrown in your cloud function.

```js
// inside your cloud function
throw new functions.https.HttpsError(
  'cancelled',
  'Your error message goes here.', // <---- THIS
  { foo: 'bar' },
);
```


### details
[method]details returns ?any;[/method]

Extra data thrown with your error on your cloud function.

```js
// inside your cloud function
throw new functions.https.HttpsError(
  'cancelled',
  'Your error message goes here.',
  { foo: 'bar' }, // <---- THIS
);
```

## Types

### FunctionsErrorCode

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