# Authentication

```
firebase.auth
```

## Methods 

### onAuthStateChanged
[method]onAuthStateChanged(listener) returns function;[/method]

Adds an observer for changes to the user's sign-in state.

Returns an unsubscriber function.

| Parameter |         |
| --------- | ------- |
| listener  | **function** |

### onIdTokenChanged
[method]onIdTokenChanged(listener) returns function;[/method]

Adds an observer for changes to the signed-in user's ID token, which includes sign-in, sign-out, and token refresh events.

Returns an unsubscriber function.

| Parameter |         |
| --------- | ------- |
| listener  | **function** |

### signOut
[method]signOut() returns Promise containing void;[/method]

Signs out the current user.
