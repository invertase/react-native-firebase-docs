# Receiving Firebase Cloud Messages

## 1) Check permissions

Before you are able to send and receive Cloud Messages, you need to ensure that the user has granted the correct permissions:

```js
const enabled = await firebase.messaging().hasPermission();
if (enabled) {
    // user has permissions
} else {
    // user doesn't have permission
}
```

or:

```js
firebase.messaging().hasPermission()
  .then(enabled => {
    if (enabled) {
      // user has permissions
    } else {
      // user doesn't have permission
    } 
  });
```

## 2) Request permissions

If the user has not already granted permissions, then you can prompt them to do so, as follows:

```js
try {
    await firebase.messaging().requestPermission();
    // User has authorised
} catch (error) {
    // User has rejected permissions
}
```

or:

```js
firebase.messaging().requestPermission()
  .then(() => {
    // User has authorised  
  })
  .catch(error => {
    // User has rejected permissions  
  });
```

## 3) Listen for FCM messages

To receive messages, we make use of the `onMessageReceived` method.  This will be triggered when the device receives a `data` only message from FCM. 

> For `notification` only or `notification + data` messages, please see the [Notifications Module](version /notifications/receiving-notifications).

```js
// Optional: Flow type
import type { RemoteMessage } from 'react-native-firebase';

componentDidMount() {
    this.messageReceivedListener = firebase.messaging().onMessageReceived(message: RemoteMessage => {
        // Process your message as required
    });
}

componentWillUnmount() {
    this.messageReceivedListener();
}
```
