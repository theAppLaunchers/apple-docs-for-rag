

- RealityKit
-  AmbientAudioComponent 

Structure

# AmbientAudioComponent

A component that configures the ambient rendering of sounds from an entity.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
struct AmbientAudioComponent
```

## Overview

Ambient audio sources emit each channel of an audio resource from an angle projected from the entity, without reverberation. Ambient audio sources take into account the relative orientation of the source and the listener. Position is not taken into account; the channels do not get louder as the user moves toward them.

The audio resource’s front channels (e.g., mono, center) are projected into the entity’s -Z direction, with the rear channels projected into +Z. The left channels are laid out in -X and the right channels are laid out in +X.

```
let entity = Entity()
let resource = try AudioFileResource.load(named: "MyAudioFile")
entity.ambientAudio = AmbientAudioComponent()
entity.playAudio(resource)
```

The `AmbientAudioComponent` allows you to set the overall level of all sounds played from the entity with the `gain` property, in relative Decibels, in the range `-.infinity ... .zero` where `-infinity` is silent and `.zero` is nominal.

```
entity.ambientAudio?.gain = -10
```

Ambient audio sources are well suited to play back multichannel content which captures the acoustics of its originating environment in the recording process (e.g., multichannel field recordings of outdoor environments).

## Topics

### Initializers

init(gain: Audio.Decibel)

Configure the behavior of an ambient audio source.

### Instance Properties

var gain: Audio.Decibel

The overall level for all sounds emitted from an entity.

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

struct SpatialAudioComponent

A component that configures how sounds emit from an entity into a person’s environment.

struct ChannelAudioComponent

A component that configures channel-based rendering of sounds from an entity.

