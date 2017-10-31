# Native Express

```
firebase.admob.NativeExpress
```

An AdMob Native Express advert is much like a standard Banner, except it can be integrated seamlessly into your app using user predefined styling (background color, positions, font size etc). Native Express adverts are exported as a usable React component.

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
| **[Size](version /admob/sizes)** | SMART_BANNER  |

### request

An instance of [ref admob.AdRequest#build]  to load with the Banner.

| Type | Default |
| --------- | ------- |
| [ref admob.AdRequest#build]   | `new AdRequest().addTestDevice().build()`  |

### video

An instance of [ref admob.VideoOptions#build] to load with the Native Express banner.

| Type | Default |
| --------- | ------- |
| [ref admob.VideoOptions#build]  | `new VideoOptions().build()`  |

### onAdLoaded

Called when an ad is received/loaded. 

| Type | Default |
| --------- | ------- |
| **function**  |  |

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
| **function**  |  |

### onVideoEnd

Called if the advert video has ended (only called if the advert has a video).

| Type | Default |
| --------- | ------- |
| **function**  |  |

### onVideoMute

Called when the video changes mute state. Returns an Object containing `{ isMuted: boolean }`.

| Type | Default |
| --------- | ------- |
| **function**  |  |

### onVideoPause

Called when video playback is paused.

| Type | Default |
| --------- | ------- |
| **function**  |  |

### onVideoPlay

Called when video playback is playing.

| Type | Default |
| --------- | ------- |
| **function**  |  |

### onVideoStart

Called when video playback first begins.

| Type | Default |
| --------- | ------- |
| **function**  |  |

## Example

```js
const NativeExpress = firebase.admob.NativeExpress;
const AdRequest = firebase.admob.AdRequest;
const request = new AdRequest();
request.addKeyword('foobar');

...
render() {
  return (
    <NativeExpress
      size={"300x400"}
      request={request.build()}
      onAdLoaded={() => {
        console.log('Advert loaded');
      }}
    />
  );
}

```
