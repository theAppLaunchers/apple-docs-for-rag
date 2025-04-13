

- External Accessory
- EAAccessoryManager
-  registerForLocalNotifications() 

Instance Method

# registerForLocalNotifications()

Begins the delivery of accessory-related notifications to the current application.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.13+tvOS 10.0+visionOS 1.0+

``` source
func registerForLocalNotifications()
```

## Discussion

Call this method to be notified when an accessory becomes connected or disconnected. The system does not send EAAccessoryDidConnectNotification and EAAccessoryDidDisconnectNotification notifications automatically, so calling this method lets the system know that your application wants to receive them. Typically, you would call this method only once early in your application, either before or after configuring your notification observers. When you no longer need to monitor these notifications, you should call the matching unregisterForLocalNotifications() method.

You can configure your notification observers either before or after calling this method. Because the shared accessory manager is the only object that sends accessory-related notifications, specifying that object or `nil` for the notification sender has the same outcome.

## See Also

### Managing Connection Status Changes

func unregisterForLocalNotifications()

Stops the delivery of accessory-related notifications to the current application.

static let EAAccessoryDidConnect: NSNotification.Name

A notification that the system sends when an accessory becomes connected and available for your application to use.

static let EAAccessoryDidDisconnect: NSNotification.Name

A notification that is posted when an accessory is disconnected and no longer available for your application to use.

let EAAccessoryKey: String

A key that indicates the accessory object whose status changed.

let EAAccessorySelectedKey: String

A key that indicates the accessory object that the user selected.

