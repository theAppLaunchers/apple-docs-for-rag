Framework

# Cinematic

Integrate playback and editing of assets captured in Cinematic mode into your app.

iOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 17.0+

## [Overview](/documentation/Cinematic#overview)

The Cinematic framework enables you to add professional-level editing and playback features to movies, recorded with the Camera app’s Cinematic mode, to your apps. These are the same features used in applications such as Final Cut Pro, Photos, and iMovie. For example, this enables your apps to change focus distance and aperture in movies, creating a bokeh effect, even after recording.

## [Topics](/documentation/Cinematic#topics)

### [Essentials](/documentation/Cinematic#Essentials)

[

Playing and editing Cinematic mode video](/documentation/cinematic/playing-and-editing-cinematic-mode-video)

Play and edit Cinematic mode video with an adjustable depth of field and focus points.

```swift
```swift
```swift
class CNScript
```
```

A collection of focus decisions, focus transitions, detections, and detection tracks associated with a movie captured in Cinematic mode and methods to change them.
```

### [Reading and rendering](/documentation/Cinematic#Reading-and-rendering)

```swift
```swift
```swift
```swift
class CNAssetInfo
```
```

An object that provides Cinematic-specific information about an asset, including its tracks.
```
```swift
```swift
```swift
class CNCompositionInfo
```
```

An object that enables you to add the appropriate number of tracks for a Cinematic asset.
```
```swift
```swift
```swift
class CNRenderingSession
```
```

An object representing the context in which rendering occurs.
```
```

### [Editing](/documentation/Cinematic#Editing)

[

Editing Spatial Audio with an audio mix](/documentation/cinematic/editing-spatial-audio-with-an-audio-mix)

Add Spatial Audio editing capabilities with the Audio Mix API in the Cinematic framework.

```swift
```swift
```swift
struct CNDetection
```
```

A structure that represents a detected subject, face, torso or pet at a particular time.
```
```swift
```swift
```swift
struct CNDecision
```
```

An object that represents a decision to focus on a particular detection, or group of detections, at a particular time.
```
```swift
```swift
```swift
class CNDetectionTrack
```
```

An object representing a series of detections of the same subject over time.
```
```swift
```swift
```swift
class CNFixedDetectionTrack
```
```

An object representing the fixed detection track.
```
```swift
```swift
```swift
class CNCustomDetectionTrack
```
```

An object representing a discrete detection track composed of individual detections.
```
```swift
```swift
```swift
enum CNDetectionType
```
```

The type of object detected, such as face, torso, cat, dog and so on.
```

### [Custom Object Tracking](/documentation/Cinematic#Custom-Object-Tracking)

```swift
```swift
```swift
```swift
struct CNBoundsPrediction
```
```

A structure representing the bounds of the predicted subject.
```
```swift
```swift
```swift
class CNObjectTracker
```
```

An object that converts a normalized point or rectangle into a detection track that tracks an object over time.
```
```

### [Structures](/documentation/Cinematic#Structures)

```swift
```swift
```swift
```swift
struct CNCinematicError
```
```
```
```

### [Reference](/documentation/Cinematic#Reference)

[

API Reference

Cinematic Enumerations](/documentation/cinematic/cinematic-enumerations)

[

API Reference

Cinematic Constants](/documentation/cinematic/cinematic-constants)

[

API Reference

Cinematic Data Types](/documentation/cinematic/cinematic-data-types)

### [Classes](/documentation/Cinematic#Classes)

```swift
```swift
```swift
```swift
class CNAssetSpatialAudioInfo
```
```
```
```

### [Enumerations](/documentation/Cinematic#Enumerations)

```swift
```swift
```swift
```swift
enum CNSpatialAudioContentType
```
```
Beta
```
```swift
```swift
```swift
enum CNSpatialAudioRenderingStyle
```
```
Beta
```
```