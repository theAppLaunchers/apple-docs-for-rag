

- Core MIDI
-  MIDIExternalDeviceCreate(\_:\_:\_:\_:) 

Function

# MIDIExternalDeviceCreate(\_:\_:\_:\_:)

Creates an external MIDI device.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+macOS 10.1+visionOS 1.0+

``` source
func MIDIExternalDeviceCreate(
    _ name: CFString,
    _ manufacturer: CFString,
    _ model: CFString,
    _ outDevice: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`name`  

The name of the device to create.

`manufacturer`  

The name of the device’s manufacturer.

`model`  

The model name of the device.

`outDevice`  

On successful return, this points to the newly created device.

## Return Value

An `OSStatus` result code.

## Discussion

Non-drivers may call this function to create external devices.

## See Also

### Managing External Devices

func MIDISetupAddExternalDevice(MIDIDeviceRef) -> OSStatus

Adds an external MIDI device to the current MIDI setup.

func MIDISetupRemoveExternalDevice(MIDIDeviceRef) -> OSStatus

Removes an external MIDI device from the current MIDI setup.

