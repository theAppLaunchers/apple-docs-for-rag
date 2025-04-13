

- CloudKit
- CKSubscription
- CKSubscription.NotificationInfo
-  shouldSendMutableContent 

Instance Property

# shouldSendMutableContent

A Boolean value that indicates whether the push notification sets the mutable content flag.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
var shouldSendMutableContent: Bool { get set }
```

## Discussion

When this property is true, the server includes the `mutable-content` flag with a value of `1` in the push notification’s payload. When the value is `1`, the system passes the notification to your app extension for modification before delivery.

See Generating a remote notification for more information about the `mutable-content` flag, and Modifying content in newly delivered notifications for information about how to modify push notifiction content in your app extension prior to delivery.

The default value of this property is false.

## See Also

### Accessing the Notification Info

var shouldSendContentAvailable: Bool

A Boolean value that indicates whether the push notification includes the content available flag.

