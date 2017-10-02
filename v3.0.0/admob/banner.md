# Banner

```
firebase.admob.Banner
```

AdMob Banners in RNFirebase are exported as a usable React component, allowing you to integrate it easily into your existing app very easily.

## Props

### unitId (required)

Your AdMob banner unit ID

| Type | Default |
| --------- | ------- |
| **string** |   |

### size

Requests and shows the banner at a certain size.

| Type | Default |
| --------- | ------- |
| [Size](version /admob/sizes) | SMART_BANNER  |

### request

An instance of [AdRequest.build](version /admob/adrequest) to load with the Banner.

| Type | Default |
| --------- | ------- |
| [AdRequest.build](version /admob/adrequest)   | `new AdRequest().addTestDevice().build()`  |

### onAdLoaded

Called when an ad is received/loaded. 

| Type | Default |
| --------- | ------- |
| function  |  |

### onAdOpened

Called when an ad opens an overlay that covers the screen.

| Type | Default |
| --------- | ------- |
| **function**  |  |

### onAdLeftApplication

Called when an ad leaves the application (e.g. to go to the browser).

| Type | Default |
| --------- | ------- |
| function  |  |

### onAdClosed

Called when the user is about to return to the application after clicking on an ad.

| Type | Default |
| --------- | ------- |
| function  |  |

### onAdFailedToLoad

Called when an ad request failed. See [Error Handling](version /admob/error-handling).

| Type | Default |
| --------- | ------- |
| function  |  |

## Additional Props

Any additional props passed through to the component must be [ViewPropTypes](https://facebook.github.io/react-native/docs/viewproptypes.html).

A common request is how to handle custom touch events of the Banner. We recommend wrapping the Banner component another component, such as a [`TouchableWithoutFeedback`](https://facebook.github.io/react-native/docs/touchablewithoutfeedback.html).

```js
...
render() {
  return (
    <TouchableWithoutFeedback
      onPress={() => this.onBannerPress()}
    >
      <Banner ... />
    </TouchableWithoutFeedback>
  );
}
```

## Example

```js
const Banner = firebase.admob.Banner;
const AdRequest = firebase.admob.AdRequest;
const request = new AdRequest();
request.addKeyword('foobar');

...
render() {
  return (
    <Banner
      size={"LARGE_BANNER"}
      request={request.build()}
      onAdLoaded={() => {
        console.log('Advert loaded');
      }}
    />
  );
}
```
