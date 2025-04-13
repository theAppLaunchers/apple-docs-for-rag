

- IOBluetooth
- IOBluetoothOBEXSession
-  withDevice(\_:channelID:) 

Type Method

# withDevice(\_:channelID:)

Creates a Bluetooth-based OBEX Session using a Bluetooth device and a Bluetooth RFCOMM channel ID.

macOS

``` source
class func withDevice(
    _ inDevice: IOBluetoothDevice!,
    channelID inRFCOMMChannelID: BluetoothRFCOMMChannelID
) -> Self!
```

## Parameters 

`inDevice`  

A valid Bluetooth device describing which device you want to connect to with Bluetooth/OBEX.

`inRFCOMMChannelID`  

An RFCOMM Channel ID numbe that is available on the remote device. This channel will be used when the transport connection is attempted.

## Discussion

Note that this does NOT mean the transport connection was open. It will be opened when OBEXConnect is invoked on the session object.

*IMPORTANT NOTE* In Bluetooth framework version 1.0.0, the session returned will NOT be autoreleased as it should be according to objc convention. This has been changed starting in Bluetooth version 1.0.1 and later, so it WILL be autoreleased upon return, so you will need to retain it if you want to reference it later.

