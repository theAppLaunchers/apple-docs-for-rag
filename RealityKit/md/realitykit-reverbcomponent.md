

- RealityKit
-  ReverbComponent 

Structure

# ReverbComponent

A component that defines the reverberation of spatial audio sources.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
struct ReverbComponent
```

## Overview

Bring your spatial audio to life by setting a reverb appropriate for your immersive environment. In visionOS, an acoustic simulation of a person’s real environment reverberates the spatial audio sources by default. When presenting your content in progressive and full immersive spaces, consider setting a reverb component to make your spatial audio sound like it exists within the environment that your visuals represent.

For example, a desert, living room, and concert hall each have unique acoustical characteristics. When the visuals and acoustic properties of sounds in your content are congruent, the environment becomes more effective as a whole.

```
// Create an entity to hold the reverb component and
// use the concert hall preset.
let reverbEntity = Entity()
reverbEntity.components.set(ReverbComponent(reverb: .preset(.concertHall)))

// Add the reverb entity to the reality view.
content.add(reverbEntity)

// Load an audio file of a violin.
if let violin = try? await AudioFileResource(named: "violin") {

    // Create an entity for playing the violin audio and
    // set the spatial audio component.
    let violinEntity = Entity()
    violinEntity.components.set(
        SpatialAudioComponent(
            directivity: .beam(focus: 0.2)
        )
    )
    violinEntity.playAudio(violin)

    // Add the violin entity to the reality view.
    content.add(violinEntity)
}
```

Use the reverbLevel property to adjust the level of audio you send to the spatial modeler. Use the directLevel property to adjust the level of audio you send directly to a person’s ears, without additional reverberation. Use the directivity property to define the pattern that disperses sound into the acoustic environment.

In macOS and iOS, only one `ReverbComponent` can be active at a time per ARView or RealityView. In visionOS, a `ReverbComponent` is only active while an app has a progressive or full immersive space open.

When the content is within a progressive immersive space, the Digital Crown adjusts how RealityKit blends:

- The acoustics simulation of a person’s real-world environment

- The reverberation the `ReverbComponent` generates

When your app is in a Shared Space WindowGroup or an ImmersiveSpace using a mixed style, RealityKit reverberates the spatial audio from the acoustics simulation and ignores the reverberation from the `ReverbComponent`.

## Topics

### Operators

static func == (ReverbComponent, ReverbComponent) -> Bool

Returns a Boolean value indicating whether two values are equal.

### Initializers

init(reverb: Reverb)

Creates a component from a reverberation setting.

### Instance Properties

var hashValue: Int

The hash value.

var reverb: Reverb

A reverberation setting the component applies to spatial audio.

### Instance Methods

func hash(into: inout Hasher)

Hashes the essential components of this value by feeding them into the given hasher.

### Default Implementations

Component Implementations

Equatable Implementations

## Relationships

### Conforms To

- Component
- Equatable
- Hashable
- Sendable

## See Also

### Reverb

struct Reverb

The reverberation RealityKit applies to spatial audio sources.

struct Preset

Reverbs defined by a preset environment.

