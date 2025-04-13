

- AVFAudio
-  AVAudioUnitComponent 

Class

# AVAudioUnitComponent

An object that provides details about an audio unit.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+

``` source
class AVAudioUnitComponent
```

## Overview

Details can include information such as type, subtype, manufacturer, and location. An `AVAudioUnitComponent` can include user tags, which you can query later for display.

## Topics

### Getting the audio unit component’s audio unit

var audioComponent: AudioComponent

The underlying audio component.

### Getting audio unit component information

var audioComponentDescription: AudioComponentDescription

The audio component description.

var availableArchitectures: [NSNumber]

An array of architectures that the audio unit supports.

var configurationDictionary: [String : Any]

The audio unit component’s configuration dictionary.

var hasCustomView: Bool

A Boolean value that indicates whether the audio unit component has a custom view.

var hasMIDIInput: Bool

A Boolean value that indicates whether the audio unit component has MIDI input.

var hasMIDIOutput: Bool

A Boolean value that indicates whether the audio unit component has MIDI output.

var manufacturerName: String

The name of the manufacturer of the audio unit component.

var name: String

The name of the audio unit component.

var passesAUVal: Bool

A Boolean value that indicates whether the audio unit component passes the validation tests.

var isSandboxSafe: Bool

A Boolean value that indicates whether the audio unit component is safe for sandboxing.

func supportsNumberInputChannels(Int, outputChannels: Int) -> Bool

Gets a Boolean value that indicates whether the audio unit component supports the specified number of input and output channels.

var typeName: String

The audio unit component type.

var version: Int

The audio unit component version number.

var versionString: String

A string that represents the audio unit component version number.

var componentURL: URL?

The URL of the audio unit component.

Deprecated

### Getting audio unit component tags

var iconURL: URL?

The URL of an icon that represents the audio unit component.

var icon: UIImage?

An icon that represents the component.

var localizedTypeName: String

The localized type name of the component.

var allTagNames: [String]

An array of tag names for the audio unit component.

var userTagNames: [String]

An array of tags the user creates.

### Audio unit manufacturer names

let AVAudioUnitManufacturerNameApple: String

The audio unit manufacturer is Apple.

### Audio unit types

let AVAudioUnitTypeOutput: String

An audio unit type that represents an output.

let AVAudioUnitTypeMusicDevice: String

An audio unit type that represents a music device.

let AVAudioUnitTypeMusicEffect: String

An audio unit type that represents a music effect.

let AVAudioUnitTypeFormatConverter: String

An audio unit type that represents a format converter.

let AVAudioUnitTypeEffect: String

An audio unit type that represents an effect.

let AVAudioUnitTypeMixer: String

An audio unit type that represents a mixer.

let AVAudioUnitTypePanner: String

An audio unit type that represents a panner.

let AVAudioUnitTypeGenerator: String

An audio unit type that represents a generator.

let AVAudioUnitTypeOfflineEffect: String

An audio unit type that represents an offline effect.

let AVAudioUnitTypeMIDIProcessor: String

An audio unit type that represents a MIDI processor.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Component management

class AVAudioUnitComponentManager

An object that provides a way to search and query audio components that the system registers.

