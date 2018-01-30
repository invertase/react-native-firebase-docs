# OAuthProvider

```
firebase.auth.OAuthProvider
```

## Properties

### PROVIDER_ID
[method]PROVIDER_ID returns string;[/method]

### providerId
[method]providerId returns string;[/method]

## Methods

### credential
[method]credential(idToken, accessToken) returns [ref auth.OAuthCredential][/method]

| Parameter |         |
| --------- | ------- |
| idToken  | **string** |
| accessToken  | **string** |

#### Example

```js
const cred = firebase.auth.OAuthProvider.credential(
    idToken,
    accessToken
);
```
