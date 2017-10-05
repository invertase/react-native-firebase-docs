# TwitterAuthProvider

```
firebase.auth.TwitterAuthProvider
```

## Properties

### PROVIDER_ID
[method]PROVIDER_ID returns string;[/method]

## Methods

### credential
[method]credential(token, secret) returns [AuthCredential](version /auth/auth-credential)[/method]

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
