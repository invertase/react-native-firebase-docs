# IOSNotifications

This deals with iOS-specific Notification functionality.

## Methods

The following methods are accessed via the IOSNotifications instance `firebase.notifications().ios`

### setCategories
[method]setCategories(categories) returns Promise;[/method]

Registers your app’s notification types and the custom actions that they support.

| Parameter |         |
| --------- | ------- |
| categories   | **Array<[ref notifications.IOSCategory]>**  |
