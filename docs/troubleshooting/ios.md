# iOS Troubleshooting

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
