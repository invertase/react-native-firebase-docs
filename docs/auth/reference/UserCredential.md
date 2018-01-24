# UserCredential

A structure containing a User, an AuthCredential, the operationType, and any additional user information that was returned from the identity provider. operationType could be 'signIn' for a sign-in operation, 'link' for a linking operation and 'reauthenticate' for a reauthentication operation.

## Properties

### user
[method]user returns nullable [ref auth.User];[/method]

### additionalUserInfo
[method]additionalUserInfo returns nullable [ref auth.AdditionalUserInfo] or undefined;[/method]

## Unsupported Methods

The following methods are not supported in RNFirebase as they cannot work in the React Native environment or have a different implementation.

### credential
<!--[method]credential returns nullable [ref auth.AuthCredential];[/method]-->

### operationType
<!--[method]operationType returns nullable string or undefined;[/method]-->
