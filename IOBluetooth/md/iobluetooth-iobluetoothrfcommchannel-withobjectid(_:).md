

- IOBluetooth
- IOBluetoothRFCOMMChannel
-  withObjectID(\_:) 

Type Method

# withObjectID(\_:)

Returns the IObluetoothRFCOMMChannel with the given IOBluetoothObjectID.

macOS

``` source
class func withObjectID(_ objectID: IOBluetoothObjectID) -> Self!
```

## Parameters 

`objectID`  

IOBluetoothObjectID of the desired IObluetoothRFCOMMChannel.

## Return Value

Returns the IObluetoothRFCOMMChannel that matches the given IOBluetoothObjectID if one exists. If no matching RFCOMM channel exists, nil is returned.

## Discussion

The IOBluetoothObjectID can be used as a global reference for a given IObluetoothRFCOMMChannel. It allows two separate applications to refer to the same IObluetoothRFCOMMChannel object.

