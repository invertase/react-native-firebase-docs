# EmailAuthProvider

```
firebase.auth.EmailAuthProvider
```

## Properties

### PROVIDER_ID
[method]PROVIDER_ID returns string;[/method]

### providerId
[method]providerId returns string;[/method]

## Methods

### credential
[method]credential(email, password) returns [ref auth.AuthCredential];[/method]

| Parameter |         |
| --------- | ------- |
| email  | **string** <br /> Email address. |
| password  | **string** <br /> User account password. |

#### Example

```js
const cred = firebase.auth.EmailAuthProvider.credential(
    email,
    password
);
```
