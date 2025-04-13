

- IOBluetooth
- IOBluetoothDevice
-  pairedDevices() 

Type Method

# pairedDevices()

Gets an array of all of the paired devices on the system.

macOS

``` source
class func pairedDevices() -> [Any]!
```

## Return Value

Returns an array of device objects for all of the paired devices on the system. If there are no paired devices, nil is returned.

## Discussion

The resulting array contains IOBluetoothDevice objects. The paired devices are currently NOT stored per user, so this is all devices paired by any user.

NOTE: This method is only available in macOS 10.2.5 (Bluetooth v1.2) or later.

