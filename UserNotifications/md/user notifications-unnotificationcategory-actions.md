

- User Notifications
- UNNotificationCategory
-  actions 

Instance Property

# actions

The actions to display when the system delivers notifications of this type.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.14+visionOS 1.0+watchOS 3.0+

``` source
var actions: [UNNotificationAction] { get }
```

## Discussion

When displaying a notification assigned to this category, the system adds a button to the notification interface for each action in this property. The system displays these buttons after the notification’s content but before the Dismiss button.

When displaying banner notifications, the system displays only the first two actions.

## See Also

### Getting the Information

var identifier: String

The unique string assigned to the category.

var intentIdentifiers: [String]

The intents related to notifications of this category.

var hiddenPreviewsBodyPlaceholder: String

The placeholder text to display when the system disables notification previews for the app.

var categorySummaryFormat: String

A format string for the summary description used when the system groups the category’s notifications.

