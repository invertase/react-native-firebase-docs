# FacebookAuthProvider

```
firebase.auth.FacebookAuthProvider
```

## Properties

### PROVIDER_ID
[method]PROVIDER_ID returns string;[/method]

## Methods

### credential
[method]credential(token) returns [AuthCredentia](version /auth/auth-credential)[/method]

| Parameter |         |
| --------- | ------- |
| token  | **string** <br /> Facebook accessToken. |

#### Example

```js
const cred = firebase.auth.FacebookAuthProvider.credential(
    accessToken
);
```
