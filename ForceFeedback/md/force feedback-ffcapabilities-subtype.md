

- Force Feedback
- FFCAPABILITIES
-  subType 

Instance Property

# subType

The force-feedback subcategory which best identifies the device’s FF capabilities.

Mac Catalyst 13.0+macOS 10.2+

``` source
var subType: UInt32
```

## Discussion

This value can be one of the following:

FFCAP_ST_KINESTHETIC

A kinesthetic force-feedback device is one that can produce “grounded” forces based on the controller’s position. It supports temporal force-feedback effects (periodic vibrations), as well as directional (constant force) and position-based (spring, damper) forces. Most higher-end force-feedback joysticks and steering wheels fall into this category.

FFCAP_ST_VIBRATION

A vibration force feedback device is one that can only produce non-grounded temporal force-feedback effects (periodic vibrations). Most console gamepads and some lower-end joysticks fall into this category.

The force-feedback subtype must be provided, and can only be one of the aforementioned values.

## See Also

### Instance Properties

var driverVer: NumVersion

Specifies the version number of the force-feedback device driver, using a NumVersion structure.

var emulatedEffects: UInt32

FFCapabilitiesEffectType flags that identify all effect types not directly supported by the device, but emulated by the plugIn.

var ffAxes: (UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8, UInt8)

An array of values that describe the axes on which force-feedback is present.

var ffSpecVer: NumVersion

Specifies the version number of the FF API specification supported by this plugIn. It should be specified using the fields of the NumVersion structure. The first version of the FF API specification is 1.0.0f0.

var firmwareVer: NumVersion

Specifies the firmware revision of the device, using a NumVersion structure.

var hardwareVer: NumVersion

Specifies the hardware revision of the device, using a NumVersion structure.

var numFfAxes: UInt32

The number of controller axes that provide force feedback. Indicates the number of valid elements in ffAxes.

var playbackCapacity: UInt32

The maximum number of created effects that can be simultaneously played via calls to FFEffectStart. This number will always be equal to or less than the storageCapacity. A device driver may allow more effects to be created than the physical device can actually handle. Therefore, this number is an important parameter for FF designers.

var storageCapacity: UInt32

The maximum number of effects that can be created via calls to FFDeviceCreateEffect and coexist at any one time. This may or may not be different from the playbackCapacity, depending on device driver complexity.

var supportedEffects: UInt32

FFCapabilitiesEffectType flags that identify all effect types supported by the plugIn/device (including driver-emulated effects).

