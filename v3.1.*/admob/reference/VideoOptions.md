# Video Options

```
firebase.admob.VideoOptions
```

The VideoOptions class is used to create an object to be passed through to each advert request. If the advert returns a video, the options are used when displaying it on the application.

?> Currently `NativeExpress` only accepts VideoOptions. If no VideoOptions are sent, the default options call `setStartMuted(true)`.

## Methods

### build
[method]build() returns object;[/method]

Builds the current video options for AdMob to handle.

### setStartMuted
[method]setStartMuted(muted) returns this;[/method]

If true, any returned video will not play sound when it starts. The end user can manually enable sound on the advert interface.

| Parameter |         |
| --------- | ------- |
| muted   | **boolean**  |

## Example

```js
const options = new firebase.admob.VideoOptions();
options.setStartMuted(false);
...

<NativeExpress
  video={options.build()}
  ...
```
