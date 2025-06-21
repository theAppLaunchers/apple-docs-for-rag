*   [WatchKit](/documentation/watchkit)
*   WKBluetoothAlertRefreshBackgroundTask

Class

# WKBluetoothAlertRefreshBackgroundTask

A task for handling timely Bluetooth alerts in the background.

watchOS 9.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class WKBluetoothAlertRefreshBackgroundTask
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/WatchKit/WKBluetoothAlertRefreshBackgroundTask#mentions)

[

Using background tasks](/documentation/watchkit/using-background-tasks)

## [Overview](/documentation/WatchKit/WKBluetoothAlertRefreshBackgroundTask#overview)

Your app can receive [`WKBluetoothAlertRefreshBackgroundTask`](/documentation/watchkit/wkbluetoothalertrefreshbackgroundtask) tasks to handle timely alerts in the background. Use these tasks to reconnect a peripheral and handle a critical alert. Apps that use timely alerts can also scan for a specific system identifier (UUID) while in the background. You can then perform the initial connection and pair the devices if necessary.

To receive timely alerts, your peripheral must use Generic Attribute Profile (GATT) transactions. Call [`setNotifyValue(_:for:)`](/documentation/CoreBluetooth/CBPeripheral/setNotifyValue\(_:for:\)) to enable notifications for the specified characteristic. Then, any changes to the peripheral’s characteristic wakes your app using a [`WKBluetoothAlertRefreshBackgroundTask`](/documentation/watchkit/wkbluetoothalertrefreshbackgroundtask) task. Use this task to reconnect to the peripheral and handle the critical alert.

Note

In watchOS 9 and later, SwiftUI Background tasks are the preferred way to handle background tasks and interactions. For more information, [`backgroundTask(_:action:)`](/documentation/SwiftUI/Scene/backgroundTask\(_:action:\)).

The critical alerts and background scans share a budget. Your app can only use five timely alerts or background scans within a rolling 24-hour window.

When your app receives a timely alert and your budget has only one Bluetooth alert task remaining, the system raises a [`leGattNearBackgroundNotificationLimit`](/documentation/CoreBluetooth/CBError-swift.struct/leGattNearBackgroundNotificationLimit) error. If you exceed the budget, it raises a [`leGattExceededBackgroundNotificationLimit`](/documentation/CoreBluetooth/CBError-swift.struct/leGattExceededBackgroundNotificationLimit) error. The system passes these errors to your [`CBPeripheralDelegate`](/documentation/CoreBluetooth/CBPeripheralDelegate), by calling methods like the [`peripheral(_:didUpdateValueFor:error:)`](/documentation/CoreBluetooth/CBPeripheralDelegate/peripheral\(_:didUpdateValueFor:error:\)-1xyna) method.

If you exceed your budget, your app doesn’t receive any timely alerts until additional background budget becomes available. The user can reset this budget by launching your app.

## [Relationships](/documentation/WatchKit/WKBluetoothAlertRefreshBackgroundTask#relationships)

### [Inherits From](/documentation/WatchKit/WKBluetoothAlertRefreshBackgroundTask#inherits-from)

*   [`WKRefreshBackgroundTask`](/documentation/watchkit/wkrefreshbackgroundtask)

### [Conforms To](/documentation/WatchKit/WKBluetoothAlertRefreshBackgroundTask#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/WatchKit/WKBluetoothAlertRefreshBackgroundTask#see-also)

### [Background tasks](/documentation/WatchKit/WKBluetoothAlertRefreshBackgroundTask#Background-tasks)

[

Using background tasks](/documentation/watchkit/using-background-tasks)

Handle scheduled update tasks in the background, and respond to background system interactions including Siri intents and incoming Bluetooth messages.

[

Preparing to take your watchOS app’s snapshot](/documentation/watchkit/preparing-to-take-your-watchos-app-s-snapshot)

Provide a timely, accurate snapshot of your app by using snapshot background tasks.

```swift
```swift
```swift
class WKApplicationRefreshBackgroundTask
```
```

A task that updates your app’s state in the background.
```
```swift
```swift
```swift
class WKURLSessionRefreshBackgroundTask
```
```

A task that responds to background URL sessions.
```
```swift
```swift
```swift
class WKWatchConnectivityRefreshBackgroundTask
```
```

A background task used to receive background updates from the Watch Connectivity framework.
```
```swift
```swift
```swift
class WKIntentDidRunRefreshBackgroundTask
```
```

A background task used to update your app after a SiriKit intent runs.
```
```swift
```swift
```swift
class WKRelevantShortcutRefreshBackgroundTask
```
```

A background task used to periodically donate relevant Siri shortcuts.
```
```swift
```swift
```swift
class WKSnapshotRefreshBackgroundTask
```
```

A background task used to update your app’s user interface in preparation for a snapshot.
```
```swift
```swift
```swift
class WKRefreshBackgroundTask
```
```

The abstract superclass for WatchKit’s background task classes.
```