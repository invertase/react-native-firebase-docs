# TwitterAuthProvider

```
firebase.auth.TwitterAuthProvider
```

## Properties

### PROVIDER_ID
[method]PROVIDER_ID returns string;[/method]

### providerId
[method]providerId returns string;[/method]

## Methods

### credential
[method]credential(token, secret) returns [ref auth.AuthCredential][/method]

| Parameter |         |
| --------- | ------- |
| token  | **string** <br /> Twitter accessToken. |
| secret  | **string** <br /> Twitter secret. |

#### Example

```js
const cred = firebase.auth.TwitterAuthProvider.credential(
    token,
    secret
);
```
