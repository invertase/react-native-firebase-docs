# JavaScript Installation/Usage

Once RNFirebase & Firebase has been setup, you can now use the library within your JavaScript like any other node module.

## Import the module

```javascript
import firebase from 'react-native-firebase';
```

As the default app is pre-initialized natively there is no need to call initializeApp for the default app instance. Just import and go:

```javascript
import firebase from 'react-native-firebase';

firebase.auth().signInAnonymously()
  .then((user) => {
    console.log(user.isAnonymous);
  });
```

## Multiple app instances

React Native Firebase supports multiple app instances. For more information see the [initializing multiple apps documentation](version /core/initialize-apps).
