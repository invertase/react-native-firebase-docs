# IOSAction

```
firebase.notifications.iOS.Action
```

See the official [iOS docs](https://developer.apple.com/documentation/usernotifications/unnotificationaction) for more information about Actions.

### Constructor
[method]new firebase.notifications.iOS.Action(actionId, title);[/method]

An IOSAction object represents a task that your app can perform in response to a delivered notification. You can define custom actions for each type of notification that your app supports. The action object itself contains information about how to display that action onscreen. When the user selects that action, the system forwards the action’s identifier string to your app so that you can perform the corresponding task.

| Parameter |         |
| --------- | ------- |
| actionId    | **string** |
| title      | **string** |

## Properties

### actionId
[method]actionId returns string;[/method]

The unique string that your app uses to identify the action.

### options
[method]options returns [ref notifications.IOSActionOptions];[/method]

The options with which to perform the action.

### title
[method]title returns string;[/method]

The localized string to use as the title of the action.

## Methods

### setOptions
[method]setOptions(options) returns [ref notifications.IOSAction];[/method]

| Parameter |         |
| --------- | ------- |
| options  | **[ref notifications.IOSActionOptions]** |

Sets the options for this action.
