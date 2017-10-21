# Social Auth

A common misconception is that RNFirebase provides social login out of the box. This is somewhat true, it leaves the implementation of the login provider up to the user and only signs the user in once the provider data has been returned.

Firebase allows a number of social providers to be used out of the box; Facebook, Google, Twitter and Github. You can however choose any provider you wish assuming they have an oAuth API.

## Facebook

Facebook provide a wrapper around their Android & iOS SDKs called [react-native-fbsdk](https://github.com/facebook/react-native-fbsdk). This module handles the flow of logging in a user and obtaining their `accessToken`. The main benefit of using the native SDK is that it detects whether the user is has the Facebook app installed and falls back to the web if not.

The `react-native-fbsdk` library allows us to first login (using `LoginManager`) and then obtain the users `accessToken` (using `AccessToken`). Once we have the access token we need to create a credential using [ref auth.FacebookAuthProvider#credential] and then sign in with that credential using [ref auth#signInWithCredential]:

```js
import { AccessToken, LoginManager } from 'react-native-fbsdk';

// ... somewhere in your login screen component
LoginManager
  .logInWithReadPermissions(['public_profile', 'email'])
  .then((result) => {
    if (result.isCancelled) {
      return Promise.reject(new Error('The user cancelled the request'));
    }
    
    console.log(`Login success with permissions: ${result.grantedPermissions.toString()}`);
    // get the access token
    return AccessToken.getCurrentAccessToken();
  })
  .then(data => {
    // create a new firebase credential with the token
    const credential = firebase.auth.FacebookAuthProvider.credential(data.accessToken);

    // login with credential
    return firebase.auth().signInWithCredential(credential);
  })
  .then((currentUser) => {
      console.warn(JSON.stringify(currentUser.toJSON()));
  })
  .catch((error) => {
    console.log(`Login fail with error: ${error}`);
  });
```

## Google

## Twitter

## Github

## Custom Provider

