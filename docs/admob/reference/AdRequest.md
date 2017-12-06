# AdRequest

```
firebase.admob.AdRequest
```

The AdRequest class is used to create an object to be passed to each advert request. The request is handled on AdMob, and returns adverts tailored to the request options provided.

If no AdRequest is sent, the default request calls addTestDevice. Therefore, ensure a custom AdRequest object is passed through in production.

## Methods

### build
[method]build() returns object;[/method]

Builds the current ad request for AdMob to handle.

### addTestDevice
[method]addTestDevice(device) returns [ref admob.AdRequest];[/method]

Sets a device ID as a test device. If no device string is passed, a default emulator id is passed.

| Parameter |         |
| --------- | ------- |
| device   | **string** (optional) <br /> Device ID. <br /> If null, a default emulator id is passed.  |

### addKeyword
[method]addKeyword(keyword) returns [ref admob.AdRequest];[/method]

Add a new keyword to relate the advert to.

| Parameter |         |
| --------- | ------- |
| keyword   | **string**  |

### setGender
[method]setGender(gender) returns [ref admob.AdRequest];[/method]

Sets the user's gender for targeting purposes.

| Parameter |         |
| --------- | ------- |
| gender   | **string** <br /> One of `male`, `female`, `unknown` |

### setRequestAgent
[method]setRequestAgent(requestAgent) returns [ref admob.AdRequest];[/method]

Sets the request agent string to identify the ad request's origin. Third party libraries that reference the Mobile Ads SDK should call this method to denote the platform from which the ad request originated. For example, if a third party ad network called "CoolAds network" mediates requests to the Mobile Ads SDK, it should call this method with "CoolAds"

| Parameter |         |
| --------- | ------- |
| requestAgent   | **string** |

### setContentUrl
[method]setContentUrl(url) returns [ref admob.AdRequest];[/method]

Sets the content URL for targeting purposes.

| Parameter |         |
| --------- | ------- |
| url   | **string** |

### tagForChildDirectedTreatment
[method]tagForChildDirectedTreatment(forChildren) returns [ref admob.AdRequest];[/method]

Sets whether the request will be shown to children.

| Parameter |         |
| --------- | ------- |
| forChildren   | **boolean** |

## Unsupported Methods

### setBirthday

### setLocation

### setIsDesignedForFamilies
