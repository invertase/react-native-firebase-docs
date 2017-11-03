# Authentication

```
firebase.auth
```

## Methods 

The following methods are accessed via the Auth instance `firebase.auth()`.

### onAuthStateChanged
[method]onAuthStateChanged(listener) returns function;[/method]

Adds an observer for changes to the user's sign-in state.

Returns an unsubscriber function.

| Parameter |         |
| --------- | ------- |
| listener  | **function([ref auth.User] or null)** |

### onUserChanged
[method]onUserChanged(listener) returns function;[/method]

> This is an experimental feature and is only part of React Native Firebase.

Adds a listener to observe changes to the [ref auth.User] object. This is a superset of everything from [ref auth.auth#onAuthStateChanged], [ref auth.auth#onIdTokenChanged] and user changes. This goal of this
method is to provide easier listening to **all** user changes such as `emailVerified` without manually having to call `.reload()`.

Returns an unsubscriber function.

| Parameter |         |
| --------- | ------- |
| listener  | **function([ref auth.User] or null)** |

[collapse Example]
```jsx
import React, { Component } from 'react';
import { View, Text } from 'react-native';
import firebase from 'react-native-firebase';

export default class MyComponent extends Component {

  componentDidMount() {
    this.unsubscribe = firebase.auth().onUserChanged(this.onUserChanged);
  }

  componentWillUnmount() {
    if (this.unsubscribe) this.unsubscribe();
  }

  onUserChanged = (currentUser) => {
    if (currentUser) {
      console.log(currentUser.toJSON())
    }
  }

  render () {
    return (
      <View>
        <Text>Hello World</Text>
      </View>
    );
  }
}
```
[/collapse]


### onIdTokenChanged
[method]onIdTokenChanged(listener) returns function;[/method]

Adds an observer for changes to the signed-in user's ID token, which includes sign-in, sign-out, and token refresh events.

Returns an unsubscriber function.

| Parameter |         |
| --------- | ------- |
| listener  | **function** |

### signOut
[method]signOut() returns Promise containing void;[/method]

Signs out the current user.

### signInAnonymously
[method]signInAnonymously() returns Promise containing [ref auth.User];[/method]

Asynchronously signs in as an anonymous user.

If there is already an anonymous user signed in, that user will be returned; otherwise, a new anonymous user identity will be created and returned.

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/operation-not-allowed   | Thrown if anonymous accounts are not enabled. Enable anonymous accounts in the Firebase Console, under the Auth tab.  |

### createUserWithEmailAndPassword
[method]createUserWithEmailAndPassword(email, password) returns Promise containing [ref auth.User];[/method]

Creates a new user account associated with the specified email address and password.

On successful creation of the user account, this user will also be signed in to your application.

User account creation can fail if the account already exists or the password is invalid.

Note: The email address acts as a unique identifier for the user and enables an email-based password reset. This function will create a new user account and set the initial user password.

| Parameter |         |
| --------- | ------- |
| email     | **string**  |
| password     | **string** |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/invalid-email  | Thrown if the email address is not valid. |
| auth/user-disabled  | Thrown if the user corresponding to the given email has been disabled. |
| auth/user-not-found | Thrown if there is no user corresponding to the given email. |
| auth/wrong-password | Thrown if the password is invalid for the given email, or the account corresponding to the email does not have a password set. |

### signInWithEmailAndPassword
[method]signInWithEmailAndPassword(email, password) returns Promise containing [ref auth.User];[/method]

Asynchronously signs in using an email and password.

Fails with an error if the email address and password do not match.

**Note:** The user's password is NOT the password used to access the user's email account. The email address serves as a unique identifier for the user, and the password is used to access the user's account in your Firebase project.

| Parameter |         |
| --------- | ------- |
| email     | **string**  |
| password     | **string** |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/invalid-email  | Thrown if the email address is not valid. |
| auth/user-disabled  | Thrown if the user corresponding to the given email has been disabled. |
| auth/user-not-found | Thrown if there is no user corresponding to the given email. |
| auth/wrong-password | Thrown if the password is invalid for the given email, or the account corresponding to the email does not have a password set. |

### signInWithCustomToken
[method]signInWithCustomToken(customToken) returns Promise containing [ref auth.User];[/method]

Asynchronously signs in using a custom token.

Custom tokens are used to integrate Firebase Auth with existing auth systems, and must be generated by the auth backend.

Fails with an error if the token is invalid, expired, or not accepted by the Firebase Auth service.

| Parameter |         |
| --------- | ------- |
| customToken     | **string**  |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/custom-token-mismatch  | Thrown if the custom token is for a different Firebase App. |
| auth/invalid-custom-token  | Thrown if the custom token format is incorrect. |

### signInWithCredential
[method]signInWithCredential(credential) returns Promise containing [ref auth.User];[/method]

Asynchronously signs in with the given credentials.

| Parameter |         |
| --------- | ------- |
| credential     | **Credential** <br /> A credential returned from a provider. |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/account-exists-with-different-credential  | Thrown if there already exists an account with the email address asserted by the credential. Resolve this by calling [ref auth#fetchProvidersForEmail] and then asking the user to sign in using one of the returned providers. Once the user is signed in, the original credential can be linked to the user with [ref auth.User#linkWithCredential]. |
| auth/invalid-credential  | Thrown if the credential is malformed or has expired. |
| auth/operation-not-allowed  | Thrown if the type of account corresponding to the credential is not enabled. Enable the account type in the Firebase Console, under the Auth tab. |
| auth/user-disabled  | Thrown if the user corresponding to the given credential has been disabled. |
| auth/user-not-found  | Thrown if signing in with a credential from [ref auth.EmailAuthProvider#credential] and there is no user corresponding to the given email. |
| auth/wrong-password  | Thrown if signing in with a credential from [ref auth.EmailAuthProvider#credential] and the password is invalid for the given email, or if the account corresponding to the email does not have a password set. |
| auth/invalid-verification-code  | Thrown if the credential is a [ref auth.PhoneAuthProvider#credential] and the verification code of the credential is not valid. |
| auth/invalid-verification-id  | Thrown if the credential is a [ref auth.PhoneAuthProvider#credential] and the verification ID of the credential is not valid. |

### signInWithPhoneNumber
[method]signInWithPhoneNumber(phoneNumber) returns Promise containing [ref auth.ConfirmationResult];[/method]

Asynchronously signs in using a phone number.

Returns a [ref auth.ConfirmationResult]. Use [ref auth.ConfirmationResult#confirm] with the verification code to confirm the phone number. In case of Android auto verification, use [ref auth#onAuthStateChanged] to listen incase the SMS is not shown to the user. See [this guide](version /auth/phone-auth#signInWithPhoneNumber) for more information.

| Parameter |         |
| --------- | ------- |
| phoneNumber | **string** <br /> Phone number containing country code (e.g. +44) |

#### Error Codes

TODO

### verifyPhoneNumber
[method]verifyPhoneNumber(phoneNumber) returns TODO;[/method]

TODO

| Parameter |         |
| --------- | ------- |
| credential     | **string** <br /> Phone number containing country code |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/invalid-email  | Thrown if the email address is not valid. |
| auth/user-not-found | Thrown if there is no user corresponding to the email address. |

### sendPasswordResetEmail
[method]sendPasswordResetEmail(email) returns Promise containing void;[/method]

Sends a password reset email to the given email address.

To complete the password reset, call [ref auth#confirmPasswordReset] with the code supplied in the email sent to the user, along with the new password specified by the user.

| Parameter |         |
| --------- | ------- |
| email     | **string** |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/invalid-email  | Thrown if the email address is not valid. |
| auth/user-not-found | Thrown if there is no user corresponding to the email address. |

### confirmPasswordReset
[method]confirmPasswordReset(code, newPassword) returns Promise containing void;[/method]

Completes the password reset process, given a confirmation code and new password.

| Parameter |         |
| --------- | ------- |
| code     | **string** |
| newPassword  | **string** |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/expired-action-code  | Thrown if the password reset code has expired. |
| auth/invalid-action-code | Thrown if the password reset code is invalid. This can happen if the code is malformed or has already been used. |
| auth/user-disabled  | Thrown if the user corresponding to the given password reset code has been disabled. |
| auth/user-not-found  | Thrown if there is no user corresponding to the password reset code. This may have happened if the user was deleted between when the code was issued and when this method was called. |
| auth/weak-password  | Thrown if the new password is not strong enough. |

### applyActionCode
[method]applyActionCode(code) returns Promise containing void;[/method]

Applies a verification code sent to the user by email or other out-of-band mechanism.

| Parameter |         |
| --------- | ------- |
| code     | **string** <br /> A verification code sent to the user. |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/expired-action-code  | Thrown if the password reset code has expired. |
| auth/invalid-action-code | Thrown if the password reset code is invalid. This can happen if the code is malformed or has already been used. |
| auth/user-disabled  | Thrown if the user corresponding to the given password reset code has been disabled. |
| auth/user-not-found  | Thrown if there is no user corresponding to the password reset code. This may have happened if the user was deleted between when the code was issued and when this method was called. |

### checkActionCode
[method]checkActionCode(code) returns Promise containing [ref auth.ActionCodeInfo];[/method]

Checks a verification code sent to the user by email or other out-of-band mechanism.

Returns metadata about the code.

| Parameter |         |
| --------- | ------- |
| code     | **string** <br /> A verification code sent to the user. |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/expired-action-code  | Thrown if the password reset code has expired. |
| auth/invalid-action-code | Thrown if the password reset code is invalid. This can happen if the code is malformed or has already been used. |
| auth/user-disabled  | Thrown if the user corresponding to the given password reset code has been disabled. |
| auth/user-not-found  | Thrown if there is no user corresponding to the password reset code. This may have happened if the user was deleted between when the code was issued and when this method was called. |

### fetchProvidersForEmail
[method]fetchProvidersForEmail(email) returns Promise containing Array of string;[/method]

Gets the list of provider IDs that can be used to sign in for the given email address. Useful for an "identifier-first" sign-in flow.

| Parameter |         |
| --------- | ------- |
| email     | **string** |

#### Error Codes

| Code | Message |
| --------- | ------- |
| auth/invalid-email  | Thrown if the email address is not valid. |

## Properties

The following properties are accessed via the Auth instance `firebase.auth()`.

### currentUser
[method]currentUser returns [ref auth.User] or null;[/method]

The currently signed-in user (or null if no user signed in).

## Unsupported Methods

The following methods are not supported in RNFirebase as they cannot work in the React Native environment or have a different implementation.

### getRedirectResult

### setPersistence

### signInAndRetrieveDataWithCredential

### signInWithPopup

### signInWithRedirect
