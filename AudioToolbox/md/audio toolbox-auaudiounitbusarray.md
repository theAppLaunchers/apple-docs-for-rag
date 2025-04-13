

- Audio Toolbox
-  AUAudioUnitBusArray 

Class

# AUAudioUnitBusArray

A class that defines a container for an audio unit’s input or output busses.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
class AUAudioUnitBusArray
```

## Overview

Hosts can observe a bus property across all busses by using KVO on a bus array object, without having to observe it on each individual bus. Some audio units (e.g. mixers) support variable numbers of busses, via subclassing. When the bus count changes, a KVO notification is sent on the audio unit’s inputBusses or outputBusses property, as appropriate.

This version 3 class is bridged to the version 2 `kAudioUnitProperty_ElementCount` API.

Note

You could add listeners to individual busses, but that means you have to observe bus count changes and add or remove listeners in response. Furthermore, the addObserver(_:toObjectsAt:forKeyPath:options:context:) method is problematic; it does not let the individual objects override the observation request, and so a bus which is proxying a bus in an extension process does not get the message.

## Topics

### Initialization

convenience init(audioUnit: AUAudioUnit, busType: AUAudioUnitBusType)

Initializes an empty bus array.

init(audioUnit: AUAudioUnit, busType: AUAudioUnitBusType, busses: [AUAudioUnitBus])

Initializes a bus array by making a copy of the supplied busses.

### Bus Array Methods and Properties

var count: Int

The number of busses in the array.

var isCountChangeable: Bool

Determines whether the array can have a variable number of busses.

var ownerAudioUnit: AUAudioUnit

The audio unit that owns the bus array.

var busType: AUAudioUnitBusType

Determines whether the bus array is for input or output.

subscript(Int) -> AUAudioUnitBus

Returns the bus at the specified index.

func setBusCount(Int) throws

Changes the number of busses in the array.

func addObserver(toAllBusses: NSObject, forKeyPath: String, options: NSKeyValueObservingOptions, context: UnsafeMutableRawPointer?)

Adds a KVO observer for a given property on all busses in the array.

func removeObserver(fromAllBusses: NSObject, forKeyPath: String, context: UnsafeMutableRawPointer?)

Removes a KVO observer for a given property on all busses in the array.

### Audio Unit Implementations

This method is only of interest to audio unit subclasses.

func replaceBusses([AUAudioUnitBus])

Replaces the current bus array with a copy of the supplied bus array.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSFastEnumeration
- NSObjectProtocol

## See Also

### Audio Units

Creating an audio unit extension

Build an extension by using an Xcode template.

Creating custom audio effects

Add custom audio-effect processing to apps like Logic Pro X and GarageBand by creating Audio Unit (AU) plug-ins.

Incorporating Audio Effects and Instruments

Add custom audio processing and MIDI instruments to your app by hosting Audio Unit (AU) plug-ins.

Debugging Out-of-Process Audio Units on Apple Silicon

Connect to out-of-process audio units using the Xcode debugger.

class AUAudioUnit

A class that defines a host’s interface to an audio unit.

class AUAudioUnitBus

A class that defines an input or output connection point on an audio unit.

class AUAudioUnitPreset

A class that describes an interface for custom parameter settings provided by the audio unit developer.

class AUAudioUnitV2Bridge

A class that wraps a version 2 audio unit as version 3 audio unit.

func AudioUnitExtensionCopyComponentList(CFString) -> Unmanaged&lt;CFArray>?

Returns the component registrations for a given audio unit extension.

func AudioUnitExtensionSetComponentList(CFString, CFArray?) -> OSStatus

Allows the implementor of an audio unit extension to dynamically modify the list of component registrations for the extension.

protocol AUAudioUnitFactory

An object that creates a version 3 audio unit.

