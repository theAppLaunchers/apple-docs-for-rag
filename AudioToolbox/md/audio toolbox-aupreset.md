

- Audio Toolbox
-  AUPreset 

Structure

# AUPreset

Used to set factory presets for an audio unit.

iOSiPadOSMac CatalystmacOStvOSvisionOS

``` source
struct AUPreset
```

## Topics

### Initializers

init()

init(presetNumber: Int32, presetName: Unmanaged&lt;CFString>?)

### Instance Properties

var presetName: Unmanaged&lt;CFString>?

If a factory preset, the name of the specified factory preset.

var presetNumber: Int32

If less than `0`, then the preset is a user preset. If greater than or equal to `0`, then this field is used to select a factory preset.

## Relationships

### Conforms To

- BitwiseCopyable

## See Also

### Structures

struct AudioUnitConnection

An audio unit source-to-destination connection specification.

struct AudioUnitEvent

struct AudioUnitExternalBuffer

Allows an audio unit host application to tell an audio unit to use a specified buffer for its input callback.

struct AudioUnitFrequencyResponseBin

An audio unit’s audio level at a particular frequency.

struct AudioUnitMeterClipping

Audio clipping that has occurred in a mixer unit.

struct AudioUnitMIDIControlMapping

struct AudioUnitOtherPluginDesc

struct AudioUnitParameter

An adjustable audio unit attribute such as volume, pitch, or filter cutoff frequency.

struct AudioUnitParameterEvent

A scheduled change to an audio unit parameter’s value.

struct AudioUnitParameterHistoryInfo

The suggested update rate and history duration for parameters which have the flag_PlotHistory flag set.

struct AudioUnitParameterNameInfo

A short version of the name for an audio unit parameter.

typealias AudioUnitParameterIDName

A type definition for a data type that defines the short version of the name for an audio unit parameter.

struct AudioUnitParameterInfo

struct AudioUnitParameterOptions

Value options for audio unit parameters.

struct AudioUnitParameterStringFromValue

A string representation of a parameter’s value.

