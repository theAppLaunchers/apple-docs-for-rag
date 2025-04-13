

- User Notifications
- UNNotificationCategory
-  init(identifier:actions:intentIdentifiers:options:) 

Initializer

# init(identifier:actions:intentIdentifiers:options:)

Creates a category object containing the specified actions and options.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.14+visionOS 1.0+watchOS 3.0+

``` source
convenience init(
    identifier: String,
    actions: [UNNotificationAction],
    intentIdentifiers: [String],
    options: UNNotificationCategoryOptions = []
)
```

## Parameters 

`identifier`  

The unique identifier for the category. Each category that your app uses must have a unique identifier. Don’t specify an empty string.

`actions`  

The actions to display when the system delivers notifications of this type. When minimal space is available, the system displays only the first two actions in the array. You may specify an empty array for this parameter if you don’t want to display custom actions.

`intentIdentifiers`  

The intent identifier strings that you want to associate with notifications of this type. The Intents framework defines constants for each type of intent that you can associate with your notifications.

`options`  

Additional options for handling notifications of this type. For a list of possible values, see UNNotificationCategoryOptions.

## Return Value

An initialized category object.

## See Also

### Essentials

convenience init(identifier: String, actions: [UNNotificationAction], intentIdentifiers: [String], hiddenPreviewsBodyPlaceholder: String, options: UNNotificationCategoryOptions)

Creates a category object containing the specified actions, options, and placeholder text used when previews aren’t shown.

convenience init(identifier: String, actions: [UNNotificationAction], intentIdentifiers: [String], hiddenPreviewsBodyPlaceholder: String?, categorySummaryFormat: String?, options: UNNotificationCategoryOptions)

Creates a category object containing the specified actions, options, placeholder text used when previews aren’t shown, and summary format string.

