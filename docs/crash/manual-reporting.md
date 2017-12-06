# Manual Reporting

Out of the box, RNFirebase will catch and report any errors - both JavaScript and native. If you wish to manually report an error, this can be done using the report method.

```javascript
try {
  initSomeSDK();
} catch (e) {
  firebase.crash().log('Some SDK failed to boot!');
  firebase.crash().report(e);
}
```
