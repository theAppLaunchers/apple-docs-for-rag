Framework

# Immersive Media Support

Read and write essential Apple Immersive Video metadata.

macOS 26.0+BetavisionOS 26.0+Beta

## [Overview](/documentation/ImmersiveMediaSupport#Overview)

Immersive Media Support enables you to create custom workflows for processing Apple Immersive Video (AIV). Use it to read and write AIV-specific metadata and enable previewing content in editorial workflows.

## [Topics](/documentation/ImmersiveMediaSupport#topics)

### [Essentials](/documentation/ImmersiveMediaSupport#Essentials)

[

Authoring Apple Immersive Video](/documentation/immersivemediasupport/authoring-apple-immersive-video)

Prepare and package immersive video content for delivery.

### [Camera metadata](/documentation/ImmersiveMediaSupport#Camera-metadata)

[`actor VenueDescriptor`](/documentation/immersivemediasupport/venuedescriptor)

The Apple Immersive Media Venue Descriptor is a collection of static metadata necessary with every Apple Immersive Video.

```swift
```swift
```swift
struct ImmersiveCamera
```
```

A structure that holds the required information for an immersive media camera to process and render video frames.
```
```swift
```swift
```swift
struct ImmersiveCameraCalibration
```
```

A structure that represents immersive media camera calibration data.
```
```swift
```swift
```swift
struct ImmersiveCameraMask
```
```

A structure that holds the camera mask type information and its relevant mask name.
```
```swift
```swift
```swift
struct ImmersiveDynamicMask
```
```

A type that holds the information required to dynamically generate an immersive media mask at load time.
```
```swift
```swift
```swift
struct ImmersiveLensDefinition
```
```

This type holds the ILPD Meirives lens configuration parameters using which a camera calibration type instance can be generated.
```

### [Presentation commands](/documentation/ImmersiveMediaSupport#Presentation-commands)

```swift
```swift
```swift
```swift
protocol PresentationCommand
```
```

A set of properties that define the interface for a presentation command.
```
```swift
```swift
```swift
struct FadeCommand
```
```

A command type for color fading during immersive media playback.
```
```swift
```swift
```swift
struct FadeEnvironmentCommand
```
```

A command type for opacity fading environment backdrops during immersive media playback.
```
```swift
```swift
```swift
struct SetCameraCommand
```
```

A command type for immersive camera switching during playback.
```
```swift
```swift
```swift
struct ShotFlopCommand
```
```

A command type to flip the video frames horizontally (mirrored horizontally) during playback for the duration of the command.
```
```swift
```swift
```swift
enum PresentationCommandType
```
```

Values that represent the type of presentation command.
```
```swift
```swift
```swift
struct PresentationDescriptor
```
```

A structure that represents dynamic metadata used during playback or when outputting the metadata track for an immersive video file.
```
```swift
```swift
```swift
class PresentationDescriptorReader
```
```

An object that provides the functionality required to understand and process immersive presentation commands.
```
```

### [Parametric immersive support](/documentation/ImmersiveMediaSupport#Parametric-immersive-support)

```swift
```swift
```swift
```swift
class ParametricImmersiveAssetInfo
```
```

An object that helps convert the original wide field of view video asset to parametric immersive asset.
```
```

### [Immersive video rendering support](/documentation/ImmersiveMediaSupport#Immersive-video-rendering-support)

```swift
```swift
```swift
```swift
struct ImmersiveCameraViewModel
```
```

A view model that holds all the resources needed to render an immersive camera view.
```
```swift
```swift
```swift
struct ImmersiveVideoMask
```
```

A video mask to use during video rendering to smooth the edges of the mesh.
```
```

### [Preview](/documentation/ImmersiveMediaSupport#Preview)

```swift
```swift
```swift
```swift
class ImmersiveMediaPreviewMessagingProtocol
```
```

An object that represents the messaging protocol a remote preview sender and receiver use to communicate.
```
```

### [Validation](/documentation/ImmersiveMediaSupport#Validation)

```swift
```swift
```swift
```swift
struct AIVUValidator
```
```

A type to validate existing AIVU files to ensure that they meet the minimum requirements for AIV.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)