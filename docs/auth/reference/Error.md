# Error

An authentication error. For method-specific error codes, refer to the specific methods in the documentation. For common error codes, check the reference below. Use [ref auth.Error#code] to get the specific error code. For a detailed message, use f[ref auth.Error#message].

## Properties

### code
[method]code returns string;[/method]

Unique error code.

### message
[method]message returns string;[/method]

Complete error message.

## Common Error Codes

- `auth/app-deleted`: Thrown if the instance of FirebaseApp has been deleted.
- `auth/app-not-authorized`: Thrown if the app identified by the domain where it's hosted, is not authorized to use Firebase Authentication with the provided API key. Review your key configuration in the Google API console.
- `auth/argument-error`: Thrown if a method is called with incorrect arguments.
- `auth/invalid-api-key`: Thrown if the provided API key is invalid. Please check that you have copied it correctly from the Firebase Console.
- `auth/invalid-user-token`: Thrown if the user's credential is no longer valid. The user must sign in again.
- `auth/network-request-failed`: Thrown if a network error (such as timeout, interrupted connection or unreachable host) has occurred.
- `auth/operation-not-allowed`: Thrown if you have not enabled the provider in the Firebase Console. Go to the Firebase Console for your project, in the Auth section and the Sign in Method tab and configure the provider.
- `auth/requires-recent-login`: Thrown if the user's last sign-in time does not meet the security threshold. Use [ref auth.User#reauthenticateWithCredential] to resolve. This does not apply if the user is anonymous.
- `auth/too-many-requests`: Thrown if requests are blocked from a device due to unusual activity. Trying again after some delay would unblock.
- `auth/unauthorized-domain`: Thrown if the app domain is not authorized for OAuth operations for your Firebase project. Edit the list of authorized domains from the Firebase console.
- `auth/user-disabled`: Thrown if the user account has been disabled by an administrator. Accounts can be enabled or disabled in the Firebase Console, the Auth section and Users subsection.
- `auth/user-token-expired`: Thrown if the user's credential has expired. This could also be thrown if a user has been deleted. Prompting the user to sign in again should resolve this for either case.
- `auth/web-storage-unsupported`: Thrown if the browser does not support web storage or if the user disables them.
