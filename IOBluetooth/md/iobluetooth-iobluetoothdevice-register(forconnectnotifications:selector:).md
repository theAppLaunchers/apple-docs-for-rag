

- IOBluetooth
- IOBluetoothDevice
-  register(forConnectNotifications:selector:) 

Type Method

# register(forConnectNotifications:selector:)

Allows a client to register for device connect notifications for any connection.

macOS

``` source
class func register(
    forConnectNotifications observer: Any!,
    selector inSelector: Selector!
) -> IOBluetoothUserNotification!
```

## Parameters 

`observer`  

Target observer object

`inSelector`  

Selector to be sent to the observer when a new connection is made

## Return Value

Returns an IOBluetoothUserNotification representing the outstanding device connect notification. To unregister the notification, call -unregister on the returned IOBluetoothUserNotification object. If an error is encountered creating the notification, nil is returned. The returned IOBluetoothUserNotification object will be valid for as long as the notification is registered. It is not necessary to retain the result. Once -unregister is called on it, it will no longer be valid.

## Discussion

The given selector will be called on the target observer whenever any device connection is made. The selector should accept two arguments. The first is the user notification object. The second is the device that was connected.

