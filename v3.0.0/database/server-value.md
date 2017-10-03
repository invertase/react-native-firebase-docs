# ServerValue

```
firebase.database.ServerValue
```

## Properties

### TIMESTAMP
[method]TIMESTAMP returns non-null Object[/method]

A placeholder value for auto-populating the current timestamp (time since the Unix epoch, in milliseconds) as determined by the Firebase servers.

> This adds the Object `{ '.sv': 'timestamp' }` which Firebase converts to the server timestamp.

#### Example

```js
var sessionsRef = firebase.database().ref("sessions");

sessionsRef.push({
  startedAt: firebase.database.ServerValue.TIMESTAMP
});
```
