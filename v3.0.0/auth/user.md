# User

A user account.

## Methods

### delete
[method]delete() returns Promise containing void;[/method]

Adds an observer for changes to the user's sign-in state.

Returns an unsubscriber function.

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/requires-recent-login  | Thrown if the user's last sign-in time does not meet the security threshold. Use [firebase.User#reauthenticateWithCredential](#reauthenticatewithcredential) to resolve. This does not apply if the user is anonymous. |


... TODO Other methods

## Properties

### displayName
[method]displayName returns string or null;[/method]

The user's display name (if available).

### email
[method]email returns string or null;[/method]

The user's email address (if available).

### emailVerified
[method]emailVerified returns boolean;[/method]

Returns `true` if the user's email address has been verified.

### isAnonymous
[method]isAnonymous returns boolean;[/method]

Returns `true` if the user is anonymous.

### photoURL
[method]photoURL returns string or null;[/method]

The URL of the user's profile picture (if available).

### providerData
[method]providerData returns TODO;[/method]

TODO

### providerId
[method]providerId returns string;[/method]

The authentication provider ID for the current user. For example, 'facebook.com', or 'google.com'.

### refreshToken
[method]refreshToken returns string;[/method]

A refresh token for the user account. Use only for advanced scenarios that require explicitly refreshing tokens.

### uid
[method]uid returns string;[/method]

The user's unique ID.
