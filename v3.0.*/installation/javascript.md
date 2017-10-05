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

RNFirebase v3 supports multiple app instances out of the box. For information on usage, follow the [core documentation](version /core/reference).
