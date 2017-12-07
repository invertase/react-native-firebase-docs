# ActionCodeSettings

This is the interface that defines the required continue/state URL with optional Android and iOS bundle identifiers.

## Structure

```js
{
  android: ({ 
    packageName: string, 
    installApp: (boolean or undefined), 
    minimumVersion: (string or undefined)
  } or undefined),
  handleCodeInApp: (boolean or undefined)
  iOS: ({ 
    bundleId: string 
  } or undefined),
  url: string,
}
```
