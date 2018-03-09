# IOSAction

```
firebase.notifications.iOS.Category
```

See the official [iOS docs](https://developer.apple.com/documentation/usernotifications/unnotificationcategory) for more information about Categories.

### Constructor
[method]new firebase.notifications.iOS.Category(categoryId, intentIds);[/method]

An IOSCategory object defines a type of notification that your executable can receive. You use category objects to implement actionable notifications—that is, notifications that have action buttons that the user can select in response to the notification. Each category object you create stores the actions and other behaviours associated with a specific type of notification.

| Parameter |         |
| --------- | ------- |
| categoryId    | **string** |
| intentIds      | **Array<string>** |

## Properties

### actions
[method]actions returns Array of [ref notifications.IOSAction];[/method]

The actions to display when a notification of this type is presented.

### categoryId
[method]categoryId returns string;[/method]

The unique string assigned to the category.

### hiddenPreviewsBodyPlaceholder
[method]hiddenPreviewsBodyPlaceholder returns nullable string;[/method]

The placeholder text to display when notification previews are disabled for the app.

### intentIds
[method]intentIds returns Array of string;[/method]

The intents related to notifications of this category.

### options
[method]options returns [ref notifications.IOSCategoryOptions];[/method]

Options for how to handle notifications of this type.

## Methods

### addAction
[method]addAction(action) returns [ref notifications.IOSCategory];[/method]

| Parameter |         |
| --------- | ------- |
| action  | **[ref notifications.IOSAction]** |

Adds an action for this category.

### setHiddenPreviewsBodyPlaceholder
[method]hiddenPreviewsBodyPlaceholder(options) returns [ref notifications.IOSCategory];[/method]

| Parameter |         |
| --------- | ------- |
| hiddenPreviewsBodyPlaceholder  | **[ref notifications.IOSCategoryOptions]** |

Sets the placeholder text to display when notification previews are disabled for the app.

### setOptions
[method]setOptions(options) returns [ref notifications.IOSCategory];[/method]

| Parameter |         |
| --------- | ------- |
| options  | **[ref notifications.IOSCategoryOptions]** |

Sets the options for this category.
