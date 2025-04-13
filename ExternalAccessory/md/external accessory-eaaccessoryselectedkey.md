

- External Accessory
-  EAAccessorySelectedKey 

Global Variable

# EAAccessorySelectedKey

A key that indicates the accessory object that the user selected.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
let EAAccessorySelectedKey: String
```

## Discussion

The value assigned to this key is the EAAccessory object that the user selected. This key is included in the info dictionary when the user pairs a Bluetooth accessory with the device using the Bluetooth picker.

## See Also

### Managing Connection Status Changes

func registerForLocalNotifications()

Begins the delivery of accessory-related notifications to the current application.

func unregisterForLocalNotifications()

Stops the delivery of accessory-related notifications to the current application.

static let EAAccessoryDidConnect: NSNotification.Name

A notification that the system sends when an accessory becomes connected and available for your application to use.

static let EAAccessoryDidDisconnect: NSNotification.Name

A notification that is posted when an accessory is disconnected and no longer available for your application to use.

let EAAccessoryKey: String

A key that indicates the accessory object whose status changed.

