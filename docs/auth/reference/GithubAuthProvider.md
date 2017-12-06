# GithubAuthProvider

```
firebase.auth.GithubAuthProvider
```

## Properties

### PROVIDER_ID
[method]PROVIDER_ID returns string;[/method]

## Methods

### credential
[method]credential(token) returns [ref auth.AuthCredential];[/method]

| Parameter |         |
| --------- | ------- |
| token  | **string** <br /> Github accessToken. |

#### Example

```js
const cred = firebase.auth.GithubAuthProvider.credential(
    accessToken
);
```
