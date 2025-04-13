

- User Notifications
- UNMutableNotificationContent
-  badge 

Instance Property

# badge

The number that your app’s icon displays.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.14+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
@NSCopying
var badge: NSNumber? { get set }
```

## Discussion

Use this property to specify the number to apply to the app’s icon when the notification arrives. If your app isn’t authorized to display badge-based notifications, the system ignores this property.

Specify the number `0` to remove the current badge, if present. Specify a number greater than `0` to display a badge with that number. Specify `nil` to leave the current badge unchanged.

## See Also

### Configuring app behavior

var launchImageName: String

The name of the image or storyboard to use when your app launches because of the notification.

var targetContentIdentifier: String?

The value your app uses to determine which scene to display to handle the notification.

