# GoogleAuthProvider

```
firebase.auth.GoogleAuthProvider
```

## Properties

### PROVIDER_ID
[method]PROVIDER_ID returns string;[/method]

### providerId
[method]providerId returns string;[/method]

## Methods

### credential
[method]credential(idToken, accessToken) returns [ref auth.AuthCredential];[/method]

Creates a credential for Google. At least one of ID token and access token is required.

| Parameter |         |
| --------- | ------- |
| idToken  | **string** (optional) <br /> Google ID token. <br /> Value may be null. |
| accessToken  | **string** (optional) <br /> Google ID token. <br /> Value may be null. |

#### Example

```js
const cred = firebase.auth.GoogleAuthProvider.credential(
    idToken,
    accessToken,
);
```
