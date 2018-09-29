# iOS Installation

First ensure you have followed the [initial setup guide](version /installation/initial-setup).

## Add the pod

Add the following to your `Podfile`:

```ruby
pod 'Firebase/Auth', '~> {{ ios.firebase.auth }}'
```

Run `pod update`.

## Enable app verification

Phone authentication leaves you 2 choices:
- Silent APNs notifications
- reCAPTCHA verification

You need to follow Firebase related documentation to complete this step [Firebase-phone-auth](https://firebase.google.com/docs/auth/ios/phone-auth) otherwise app verification will throxw an error.

?> If you plan to make use of email sign-in links then you'll also need to follow the [Dynamic Links for iOS installation guide](version /links/ios).
