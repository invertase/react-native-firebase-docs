# PhoneAuthProvider

```
firebase.auth.PhoneAuthProvider
```

## Properties

### PROVIDER_ID
[method]PROVIDER_ID returns string;[/method]

## Methods

### credential
[method]credential(verificationId, code) returns [AuthCredentia](version /auth/auth-credential)[/method]

| Parameter |         |
| --------- | ------- |
| verificationId  | **string** |
| code  | **string** |

#### Example

```js
const cred = firebase.auth.PhoneAuthProvider.credential(
    verificationId,
    code
);
```
