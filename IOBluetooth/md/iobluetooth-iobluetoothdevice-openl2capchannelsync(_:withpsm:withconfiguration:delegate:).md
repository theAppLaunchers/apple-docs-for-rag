

- IOBluetooth
- IOBluetoothDevice
-  openL2CAPChannelSync(\_:withPSM:withConfiguration:delegate:) 

Instance Method

# openL2CAPChannelSync(\_:withPSM:withConfiguration:delegate:)

Opens a new L2CAP channel to the target device. Returns only after the channel is opened.

macOS

``` source
func openL2CAPChannelSync(
    _ newChannel: AutoreleasingUnsafeMutablePointer!,
    withPSM psm: BluetoothL2CAPPSM,
    withConfiguration channelConfiguration: [AnyHashable : Any]!,
    delegate channelDelegate: Any!
) -> IOReturn
```

## Parameters 

`newChannel`  

A pointer to an IOBluetoothL2CAPChannel object to receive the L2CAP channel requested to be opened. The newChannel pointer will only be set if kIOReturnSuccess is returned.

`psm`  

The L2CAP PSM value for the new channel.

`channelConfiguration`  

The dictionary that describes the initial configuration for the channel.

`channelDelegate`  

The object that will play the role of delegate for the channel. A channel delegate is the object the l2cap uses as target for data and events. The developer will implement only the the methods he/she is interested in. A list of the possible methods is at the end of the file “IOBluetoothL2CAPChannel.h” in the definition of the protocol IOBluetoothL2CAPChannelDelegate.

## Return Value

Returns kIOReturnSuccess if the open process was successfully started (or if an existing L2CAP channel was found). The channel must be released when the caller is done with it.

## Discussion

This method will begin the process of opening a new L2CAP channel to the target device. The baseband connection to the device will be opened if it is not open already. The L2CAP channel open process will not complete until the client has registered an incoming data listener on the new channel. This prevents a situation where the channel succeeds in being configured and opened and receives data before the client is listening and is ready for it. The L2CAP channel object is already retained when this function returns success; the channel must be released when the caller is done with it.

NOTE: This method is only available in macOS 10.5 (Bluetooth v2.0) or later.

