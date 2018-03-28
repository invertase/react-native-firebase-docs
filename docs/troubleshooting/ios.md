# iOS Troubleshooting

## Failing to recognize the GoogleService-Info.plist

If the `GoogleService-Info.plist` is not registered with XCode, your app will crash right after starting. You can verify the file is not registered if you open your project in Xcode and don't see the file in your app's directory listing. 

To fix this, first make sure your `GoogleService-Info.plist` from google is present in the `YOUR_APP/ios` directory. Next open Xcode and open the folder tab and then open your project. You should see the `AppDelegate.h` file and other important files. Right click on your project and click on the option that says "Add Files to YOUR_APP". Select `GoogleService-Info.plist`. You should now see it in your project. Finally, rebuild your app. 


## Duplicate Symbols / Undefined Symbols (build time error)

Unfortunately, XCode can get in a bit of a mess every now and again, particularly when updating to new versions of `react-native-firebase` or the Firebase pods.  If you get a Duplicate Symbols or Undefined Symbols error then you're likely to need to do a proper clean of your workspace.

To do this, try the following in xcode:

```javascript
1) Do product > clean
2) Close Xcode
3) Re-run pod install (from the command line)
4) Re-open the .xcworkspace
5) Do product > clean
6) Try a build
```
