# Banner

```
firebase.admob.Banner
```

AdMob Banners in RNFirebase are exported as a usable React component, allowing you to integrate it easily into your existing app very easily.

## Props

| Prop                | Type               | Default                                 | Description                                                                         |
| ------------------- | ------------------ | --------------------------------------- | ----------------------------------------------------------------------------------- |
| size (required)     | string (See [Sizes](version /admob/sizes)) | SMART_BANNER                            | Returns a sized banner (automatically sets View style)                              |
| unitId (required)   | string             |                                         | Your AdMob banner unit ID.                                                          |
| request             | [AdRequest](/admob/adrequest)          | new AdRequest().addTestDevice().build() | An instance of AdRequest to load with the Banner                                    |
| onAdLoaded          | function           |                                         | Called when an ad is received.                                                      |
| onAdOpened          | function           |                                         | Called when an ad opens an overlay that covers the screen.                          |
| onAdLeftApplication | function           |                                         | Called when an ad leaves the application (e.g., to go to the browser).              |
| onAdClosed          | function           |                                         | Called when the user is about to return to the application after clicking on an ad. |
| onAdFailedToLoad    | function           |                                         | Called when an ad request failed. See Error Handling                                |

## Additional Props

Any additional props passed through to the component must be [ViewPropTypes](https://facebook.github.io/react-native/docs/viewproptypes.html).

A common request is how to handle custom touch events of the Banner. We recommend wrapping the Banner component another component, such as a [`TouchableWithoutFeedback`](https://facebook.github.io/react-native/docs/touchablewithoutfeedback.html).

```
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

```
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
        console.log('Advert loaded and is now visible');
      }}
    />
  );
}
```
