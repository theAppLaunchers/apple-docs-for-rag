

- User Notifications
- UNNotificationContent
-  title 

Instance Property

# title

The localized text that provides the notification’s primary description.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.14+visionOS 1.0+watchOS 3.0+

``` source
var title: String { get }
```

## Discussion

When a title is present, the system attempts to display a notification alert. If your app isn’t authorized to display alert-based notifications, the system ignores this property.

Title strings should be short, usually only a couple of words describing the reason for the notification. In watchOS, the system displays the title string as part of the short look notification interface, which has limited space.

## See Also

### Accessing the primary content

var subtitle: String

The localized text that provides the notification’s secondary description.

var body: String

The localized text that provides the notification’s main content.

