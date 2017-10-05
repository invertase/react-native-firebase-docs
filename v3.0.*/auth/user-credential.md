# UserCredential

A structure containing a User, an AuthCredential, the operationType, and any additional user information that was returned from the identity provider. operationType could be 'signIn' for a sign-in operation, 'link' for a linking operation and 'reauthenticate' for a reauthentication operation.

## Properties

### user
[method]user returns nullable [User](version /auth/user)[/method]

### credential
[method]credential returns nullable [AuthCredential](version /auth/auth-credential)[/method]

### operationType
[method]operationType returns nullable string or undefined[/method]

### additionalUserInfo
[method]additionalUserInfo returns nullable [AdditionalUserInfo](version /auth/addtional-user-info) or undefined[/method]
