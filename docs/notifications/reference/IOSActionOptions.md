# IOSActionOptions

Controls behaviours to apply to an [ref notifications.IOSAction].

## Properties

### authenticationRequired
[method]authenticationRequired returns nullable boolean;[/method]

The action requires that the user’s device be unlocked. When the user selects an action with this option, the system prompts the user to unlock the device. After unlocking, the system notifies your app of the selected action. You might use option to perform actions that require accessing data that is encrypted while the device is locked.

### destructive
[method]destructive returns nullable boolean;[/method]

The action is displayed with special highlighting to indicate that it performs a destructive task. Use this option for actions that delete user data or change the app irrevocably.

### foreground
[method]foreground returns nullable boolean;[/method]

The action causes the app to launch in the foreground. When the user selects an action containing this option, the system brings the app to the foreground, asking the user to unlock the device as needed. Use this option for actions that require the user to interact further with your app. Do not use this option simply to bring your app to the foreground.
