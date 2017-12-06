# Remote Config Example

The following example shows how you'd enable a feature in your app (`enableSuperCoolFeature`) if Remote Config returns `hasExperimentalFeature` being true.

```js
if (__DEV__) {
  firebase.config().enableDeveloperMode();
}

// Set default values
firebase.config().setDefaults({
  hasExperimentalFeature: false,
});

firebase.config().fetch()
  .then(() => {
    return firebase.config().activateFetched();
  })
  .then((activated) => {
    if (!activated) console.log('Fetched data not activated');
    return firebase.config().getValue('hasExperimentalFeature');
  })
  .then((snapshot) => {
    const hasExperimentalFeature = snapshot.val();

    if(hasExperimentalFeature) {
      enableSuperCoolFeature();
    }

    // continue booting app
  })
  .catch(console.error);
```
