Framework

# AudioDriverKit

Develop drivers for audio devices.

DriverKit 21.0+

## [Overview](/documentation/AudioDriverKit#overview)

The AudioDriverKit framework supports the development of [DriverKit](/documentation/DriverKit)\-based audio extensions that communicate with the CoreAudio HAL. AudioDriverKit handles all of the necessary user client communication between the CoreAudio HAL and the driver extension, which eliminates the need to implement an audio server plug-in. You can also integrate with transport-based driver extension frameworks like [PCIDriverKit](/documentation/PCIDriverKit).

Develop your driver by subclassing [`IOUserAudioDriver`](/documentation/audiodriverkit/iouseraudiodriver). On macOS, use the [System Extensions](/documentation/SystemExtensions) framework to install and upgrade your driver. On iPadOS, the system automatically discovers and upgrades drivers along with their host apps.

Note

AudioDriverKit is available on macOS for Intel and Apple Silicon devices, and on iPadOS for devices with an M-series processor.

## [Topics](/documentation/AudioDriverKit#topics)

### [Essentials](/documentation/AudioDriverKit#Essentials)

[`IOUserAudioObject`](/documentation/audiodriverkit/iouseraudioobject)

The base class for most classes in the framework.

[`IOUserAudioDriver`](/documentation/audiodriverkit/iouseraudiodriver)

A DriverKit provider object that manages communications with an audio device.

[`DriverKit Audio Family`](/documentation/BundleResources/Entitlements/com.apple.developer.driverkit.family.audio)

A Boolean value that indicates whether the device supports audio functionality.

[

Creating an audio device driver](/documentation/audiodriverkit/creating-an-audio-device-driver)

Implement a configurable audio input source as a driver extension that runs in user space in macOS and iPadOS.

### [Working with Audio Devices](/documentation/AudioDriverKit#Working-with-Audio-Devices)

[`IOUserAudioClockDevice`](/documentation/audiodriverkit/iouseraudioclockdevice)

An audio clock device object, used to synchronize and perform I/O.

[`IOUserAudioDevice`](/documentation/audiodriverkit/iouseraudiodevice)

An audio clock device object that handles the configurations for running I/O.

### [Containing Audio Objects](/documentation/AudioDriverKit#Containing-Audio-Objects)

[`IOUserAudioBox`](/documentation/audiodriverkit/iouseraudiobox)

A container for other audio objects, typically audio devices and audio clock devices.

### [Working with Audio Streams](/documentation/AudioDriverKit#Working-with-Audio-Streams)

[`IOUserAudioStream`](/documentation/audiodriverkit/iouseraudiostream)

An audio object that performs I/O for an audio device.

### [Using Audio Controls](/documentation/AudioDriverKit#Using-Audio-Controls)

[`IOUserAudioControl`](/documentation/audiodriverkit/iouseraudiocontrol)

The base class for audio control objects.

[`IOUserAudioBooleanControl`](/documentation/audiodriverkit/iouseraudiobooleancontrol)

A control object that supports setting a Boolean value.

[`IOUserAudioStereoPanControl`](/documentation/audiodriverkit/iouseraudiostereopancontrol)

A control object that supports panning between stereo channels.

[`IOUserAudioSliderControl`](/documentation/audiodriverkit/iouseraudioslidercontrol)

A control object that supports setting a 32-bit integer value.

[`IOUserAudioSelectorControl`](/documentation/audiodriverkit/iouseraudioselectorcontrol)

A control object that supports selecting from a set of values.

[`IOUserAudioLevelControl`](/documentation/audiodriverkit/iouseraudiolevelcontrol)

A control object that supports setting an audio level, with either scalar or decibel values.

### [Supporting Types](/documentation/AudioDriverKit#Supporting-Types)

[`IOUserAudioReservedConfigChangeAction`](/documentation/audiodriverkit/audiodriverkit/iouseraudioreservedconfigchangeaction)

Identifiers for object state changes that require a configuration change.

### [Namespaces](/documentation/AudioDriverKit#Namespaces)

[`AudioDriverKit`](/documentation/audiodriverkit/audiodriverkit)

### [Macros](/documentation/AudioDriverKit#Macros)

[`DebugMsg`](/documentation/audiodriverkit/debugmsg)

[`FailIf`](/documentation/audiodriverkit/failif)

[`FailIfError`](/documentation/audiodriverkit/failiferror)

[`FailIfNULL`](/documentation/audiodriverkit/failifnull)

[`kIOUserAudioDriverUserClientType`](/documentation/audiodriverkit/kiouseraudiodriveruserclienttype)