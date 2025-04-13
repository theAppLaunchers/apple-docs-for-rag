

- PHASE
-  PHASEAmbientMixerDefinition 

Class

# PHASEAmbientMixerDefinition

An audio-layering object that outputs sound in a particular direction in 3D space.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 17.0+visionOS 1.0+

``` source
class PHASEAmbientMixerDefinition
```

## Overview

As an audio-layering object, this class combines multiple audio signals to a single signal for the output device. Play audio with a 3D orientation using this class when you supply a quaternion for the `orientation` argument of the init(channelLayout:orientation:) initializer. For information on orientation the sound, see Working with Quaternions.

You also supply the intitializer with a channel layout in either mono, stereo, or surround formats. Surround audio files create the best listening experience due to their extra channel data. The framework renders each channel from the direction of its corresponding speaker in the channel layout. This class ignores low-frequency effect channels that may be present in the layout.

Note

For one-time sounds that require no position or orientation, use PHASEChannelMixerDefinition instead of this class. If your audio playback needs to react to distance or contain environmental effects, use a spatial mixer; for more information, see Spatial Mixing.

### Play Sound with a Specific Orientation, Channel Layout, and Listener

To play ambient sound, define an orientation for the mixer and a channel layout for the source audio data. For example, the following code creates a 5.0 surround-sound ambient source from a 5.1 surround-sound asset.

- Swift
- Objective-C

```
```

```
```

Ambient mixers require the app to specify a listener, for which you define an orientation by setting the listener’s transform. Continuing on the example above, the following code completes a mixer by attaching a listener, and then plays a sound event.

- Swift
- Objective-C

```
```

```
```

PHASE changes the channel output of ambient-mixer sound dynamically, depending on the respective directions of the mixer and the listener. For example, you can use an ambient mixer in a game to play the environmental sound of birds all around and the sound of traffic on a road in just one audio channel. Depending on the direction the player is facing, the mixer can rotate the audio so that the road always sounds like it’s coming from the same direction, for example, the west.

## Topics

### Creating an Ambient Mixer

init(channelLayout: AVAudioChannelLayout, orientation: simd_quatf)

Creates an ambient mixer with the given channel layout and orientation.

convenience init(channelLayout: AVAudioChannelLayout, orientation: simd_quatf, identifier: String)

Creates a named ambient mixer with the given channel layout and orientation.

### Inspecting the Mixer

var inputChannelLayout: AVAudioChannelLayout

The channel layout of input audio.

var orientation: simd_quatf

A quaternion that describes the orientation of the speaker layout relative to the scene origin.

## Relationships

### Inherits From

- PHASEMixerDefinition

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Audio Layering and Effects

class PHASEChannelMixerDefinition

An audio-layering object that routes sound directly to the device’s output.

class PHASEMixerDefinition

An object to initialize a mixer with a given configuration.

class PHASEMixer

An object that combines multiple audio signals into a single signal.

class PHASEDefinition

A base class that adds a name to framework definitions.

Spatial Mixing

Define environmental characteristics that determine how sound plays in your app’s 3D soundscape.

