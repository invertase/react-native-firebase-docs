# EmailAuthProvider

```
firebase.auth.EmailAuthProvider
```

## Properties

### EMAIL_LINK_SIGN_IN_METHOD
[method]EMAIL_LINK_SIGN_IN_METHOD returns string;[/method]

This corresponds to the sign-in method identifier as returned in [ref auth.auth#fetchSignInMethodsForEmail].

### EMAIL_PASSWORD_SIGN_IN_METHOD
[method]EMAIL_PASSWORD_SIGN_IN_METHOD returns string;[/method]

This corresponds to the sign-in method identifier as returned in [ref auth.auth#fetchSignInMethodsForEmail].

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
const credential = firebase.auth.EmailAuthProvider.credential(
    email,
    password
);
```

### credentialWithLink
[method]credentialWithLink(email, emailLink) returns [ref auth.AuthCredential];[/method]

Initialize an EmailAuthProvider credential using an email and link.

> Ensure your link is a valid email sign-in link by calling [ref auth.auth#isSignInWithEmailLink].

| Parameter |         |
| --------- | ------- |
| email  | **string** <br /> Email address. |
| emailLink  | **string** <br /> Sign-in email link. |

#### Example

```js
const credential = firebase.auth.EmailAuthProvider.credentialWithLink(
    email,
    emailLink
);
```
