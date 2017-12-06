# iOS Installation

First ensure you have followed the [initial setup guide](version /installation/initial-setup).

## Add the pod

Add the following to your `Podfile`:

```ruby
pod 'Fabric', '~> 1.7.2'
pod 'Crashlytics', '~> 3.9.3'
```

Run `pod update`.

## Add the Crashlytics run descriptor

1. Open your project in Xcode and select its project file in the NAvigator
2. Open the **Build Phases** tab.
3. Click **+ Add a new build phase**, and select **New Run Script Phase**.
4. Add the following line to the **Type a script..** text box:

```groovy
"${PODS_ROOT}/Fabric/run"
```
