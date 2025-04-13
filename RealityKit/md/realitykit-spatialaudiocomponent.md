

- RealityKit
-  SpatialAudioComponent 

Structure

# SpatialAudioComponent

A component that configures how sounds emit from an entity into a person’s environment.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
struct SpatialAudioComponent
```

## Overview

The audio system continuously updates the position and orientation of spatial audio sources automatically, so sounds come from an entity wherever it goes and wherever it points. Spatial audio sources incorporate a person’s environment acoustics so that they blend in naturally with the surrounding area. The system distance-attenuates the spatial audio sources so they become quieter the farther away they are from the person.

Note

Spatial audio sources emit only a single channel (that is, mono). The engine mixes any stereo or multichannel audio resources down to a single channel before spatialization. To avoid any unwanted mixdown artifacts, use mono source material where possible.

RealityKit audio playback is spatial by default, so no additional configuration is necessary to opt into sophisticated spatial rendering.

```
let entity = Entity()
let resource = try AudioFileResource.load(named: "MyAudioFile")
entity.playAudio(resource) // Audio file is played spatially from entity
```

`SpatialAudioComponent` allows you to further customize the playback characteristics of spatial audio sources. The gain, directLevel, and reverbLevel properties are in relative decibels, in the range `[-Decibel.infinity, Decibel.zero]`, where `-Decibel.infinity` is silent and `Decibel.zero` is nominal.

For example, you can adjust the overall level of all sounds the entity plays with the gain property.

```
entity.spatialAudio = SpatialAudioComponent(gain: -10)
```

You can reduce the amount of reverb you apply to all sounds the entity plays with the reverbLevel property. Reduce this value to make the sounds less reverberant and more intimate. Set reverbLevel to `-Decibel.infinity` to cause the sounds to collapse into the head of the listener.

```
entity.spatialAudio?.reverbLevel = -6
```

You can update gain, directLevel, and reverbLevel properties dynamically. For example, you can update them when your app’s state changes, or in the context of a custom RealityKit system.

The directivity property allows you to configure the radiation pattern for sound that an entity emits.

```
entity.spatialAudio?.directivity = .beam(focus: 0.5)
```

Spatial audio sources project sounds along their negative z-axis. If you colocate and co-orient a spatial audio source using visual content that you author with a positive z-forward coordinate convention, you need to rotate your spatial audio source 180º about the y-axis.

```
let parent = Entity()

// Add a model entity.
let model = try ModelEntity.load(named: "PositiveZForward")
parent.addChild(model)

// Add an audio source entity.
let audioSource = Entity()
parent.addChild(audioSource)

// Orient the audio source toward +Z.
audioSource.orientation = .init(angle: .pi, axis: [0, 1, 0])
```

This is only a consideration if you explicitly set a directivity other than the default `.beam(focus: .zero)`, which projects sound evenly for all frequencies in all directions.

The distanceAttenuation property allows you to configure the way that a sound level decreases as the distance between the listener and the sound source increases.

```
entity.spatialAudio?.distanceAttenuation = .rolloff(factor: 2)
```

## Topics

### Initializers

init(gain: Audio.Decibel, directLevel: Audio.Decibel, reverbLevel: Audio.Decibel, directivity: Audio.Directivity)

Creates a spatial audio component from a gain value, a direct level, a reverb level, and a directivity value.

init(gain: Audio.Decibel, directLevel: Audio.Decibel, reverbLevel: Audio.Decibel, directivity: Audio.Directivity, distanceAttenuation: Audio.DistanceAttenuation)

Creates a spatial audio component from a gain value, a direct level, a reverb level, a directivity value, and a distance attenuation value.

### Instance Properties

var directLevel: Audio.Decibel

The level of the direct unreverberated signal that an entity emits.

var directivity: Audio.Directivity

The radiation pattern for sound that an entity emits.

var distanceAttenuation: Audio.DistanceAttenuation

A value that specifies the way that the sound level decreases as the distance between the listener and the sound source increases.

var gain: Audio.Decibel

The overall level for all sounds that an entity emits.

var reverbLevel: Audio.Decibel

The level of reverberated signal that an entity emits.

### Default Implementations

Component Implementations

Decodable Implementations

Encodable Implementations

Equatable Implementations

Hashable Implementations

## Relationships

### Conforms To

- Component
- Copyable
- Decodable
- Encodable
- Equatable
- Hashable

## See Also

### Audio source components

Creating a Spaceship game

Build an immersive game using RealityKit audio, simulation, and rendering features.

struct AmbientAudioComponent

A component that configures the ambient rendering of sounds from an entity.

struct ChannelAudioComponent

A component that configures channel-based rendering of sounds from an entity.

