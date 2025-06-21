Framework

# AVFoundation

Work with audiovisual assets, control device cameras, process audio, and configure system audio interactions.

iOS 2.2+iPadOS 13.1+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 3.0+

## [Overview](/documentation/AVFoundation#overview)

AVFoundation combines several major technology areas that together encompass a wide range of tasks for inspecting, playing, capturing, and processing audiovisual media on Apple platforms.

## [Topics](/documentation/AVFoundation#topics)

### [Essentials](/documentation/AVFoundation#Essentials)

[

AVFoundation updates](/documentation/Updates/AVFoundation)

Learn about important changes to AVFoundation.

### [Common](/documentation/AVFoundation#Common)

[

API Reference

Media assets](/documentation/avfoundation/media-assets)

Load media assets from files and streams to inspect their attributes, tracks, and embedded metadata.

[

API Reference

Media reading and writing](/documentation/avfoundation/media-reading-and-writing)

Read images from video, export to alternative formats, and perform sample-level reading and writing of media data.

[

API Reference

Media types and utilities](/documentation/avfoundation/media-types-and-utilities)

Identify the types of content and file formats that AVFoundation supports.

[

API Reference

Video settings](/documentation/avfoundation/video-settings)

Configure video processing settings using standard key and value constants.

[

API Reference

Audio settings](/documentation/avfoundation/audio-settings)

Configure audio processing settings using standard key and value constants.

### [Playback](/documentation/AVFoundation#Playback)

[

API Reference

Media playback](/documentation/avfoundation/media-playback)

Manage the playback of media assets and interstitial content, independent of how you present that content in your interface.

[

API Reference

Offline playback and storage](/documentation/avfoundation/offline-playback-and-storage)

Download streamed content to disk to allow offline playback, and define policies to automatically remove downloaded assets.

[

API Reference

Streaming and AirPlay](/documentation/avfoundation/streaming-and-airplay)

Stream content wirelessly to other devices using AirPlay, and handle requests involving FairPlay-protected assets.

[

API Reference

Sample buffer playback](/documentation/avfoundation/sample-buffer-playback)

Create custom controllers to play and synchronize the timing of sample buffer streams.

### [Capture](/documentation/AVFoundation#Capture)

[

API Reference

Capture setup](/documentation/avfoundation/capture-setup)

Configure built-in cameras and microphones, and external capture devices, for media capture.

[

API Reference

Photo capture](/documentation/avfoundation/photo-capture)

Capture high-quality still images, Live Photos, and supporting photo data.

[

API Reference

Audio and video capture](/documentation/avfoundation/audio-and-video-capture)

Capture audio and video directly to media files, or capture streams of media for direct access to media sample buffers.

[

API Reference

Additional data capture](/documentation/avfoundation/additional-data-capture)

Capture additional data including depth and metadata, and synchronize capture from multiple outputs.

### [Editing](/documentation/AVFoundation#Editing)

[

API Reference

Composite assets](/documentation/avfoundation/composite-assets)

Combine tracks and segments of tracks from multiple assets into a composite asset that you can play or process.

[

API Reference

QuickTime movies](/documentation/avfoundation/quicktime-movies)

Access the contents of a QuickTime movie file, and perform sample-level edits of its media tracks.

[

API Reference

Video effects](/documentation/avfoundation/video-effects)

Define standard video transition effects, synchronize layer animations with media timing, and create custom video compositors.

[

API Reference

Audio mixing](/documentation/avfoundation/audio-mixing)

Define how to mix the audio levels from multiple audio tracks over an asset’s duration.

### [Audio](/documentation/AVFoundation#Audio)

[

API Reference

Audio playback, recording, and processing](/documentation/avfoundation/audio-playback-recording-and-processing)

Play, record, and process audio; configure your app’s system audio behavior.

[

API Reference

Speech synthesis](/documentation/avfoundation/speech-synthesis)

Configure voices to speak strings of text.

### [Errors](/documentation/AVFoundation#Errors)

```swift
```swift
```swift
```swift
let AVFoundationErrorDomain: String
```
```

The error domain of AVFoundation errors.
```
```swift
```swift
```swift
struct AVError
```
```

A structure that defines the errors that framework operations can generate.
```
```

### [Macros](/documentation/AVFoundation#Macros)

[

API Reference

Macros](/documentation/avfoundation/avfoundation-macros)

### [Classes](/documentation/AVFoundation#Classes)

```swift
```swift
```swift
```swift
class AVCaptureSpatialAudioMetadataSampleGenerator
```
```
Beta
```
```swift
```swift
```swift
class AVCustomMediaSelectionScheme
```
```

For content that has been authored with the express intent of offering an alternative selection interface for AVMediaSelectionOptions, AVCustomMediaSelectionScheme provides a collection of custom settings for controlling the presentation of the media.

Beta
```
```swift
```swift
```swift
class AVMediaPresentationSelector
```
```

For content that has been authored with the express intent of offering an alternative selection interface for AVMediaSelectionOptions, AVMediaPresentationSelector represents a collection of mutually exclusive settings.

Beta
```
```swift
```swift
```swift
class AVMediaPresentationSetting
```
```

For content that has been authored with the express intent of offering an alternative selection interface for AVMediaSelectionOptions, AVMediaPresentationSetting represents a selectable setting for controlling the presentation of the media.

Beta
```
```swift
```swift
```swift
class AVMetadataCatHeadObject
```
```
Beta
```
```swift
```swift
```swift
class AVMetadataDogHeadObject
```
```
Beta
```
```swift
```swift
```swift
class AVMetricDownloadSummaryEvent
```
```

Represents a summary metric event with aggregated metrics for the entire download task.
```
```swift
```swift
```swift
class AVPlaybackCoordinationMedium
```
```
```
```

### [Structures](/documentation/AVFoundation#Structures)

```swift
```swift
```swift
```swift
struct AVCIImageFilteringParameters
```
```
```
```swift
```swift
```swift
struct AVCIImageFilteringResult
```
```

An output video frame processed with Core Image filtering.
```
```swift
```swift
```swift
struct AVCaptureSceneMonitoringStatus
```
```
Beta
```
```

### [Variables](/documentation/AVFoundation#Variables)

```swift
```swift
```swift
```swift
let AVAssetExportPresetHEVC4320x2160: String
```
```
Beta
```
```swift
```swift
```swift
let AVAssetExportPresetMVHEVC4320x4320: String
```
```
Beta
```
```swift
```swift
```swift
let AVAssetExportPresetMVHEVC7680x7680: String
```
```
Beta
```
```swift
```swift
```swift
let AVContentKeyRequestRandomDeviceIdentifierSeedKey: String
```
```

Value is an NSData containing a 16-byte seed to randomize the user’s deviceID contained in the SPC blob during FairPlay key exchange

Beta
```
```swift
```swift
```swift
let AVContentKeyRequestShouldRandomizeDeviceIdentifierKey: String
```
```

Value is an Boolean indicating whether the user’s deviceID contained in the SPC blob during FairPlay key exchange should be randomized using a system generated seed

Beta
```
```swift
```swift
```swift
let AVPlayerInterstitialEventMonitorCurrentEventSkippableStateDidChangeEventKey: String
```
```

The dictionary key for the AVPlayerInterstitial event that had its skippable event state changed in the payload of the AVPlayerInterstitialEventMonitorCurrentEventSkippableStateDidChangeNotification.

Beta
```
```swift
```swift
```swift
let AVPlayerInterstitialEventMonitorCurrentEventSkippableStateDidChangeSkipControlLabelKey: String
```
```

The dictionary key for the skip label of the event in the payload of the AVPlayerInterstitialEventMonitorCurrentEventSkippableStateDidChangeNotification.

Beta
```
```swift
```swift
```swift
let AVPlayerInterstitialEventMonitorCurrentEventSkippableStateDidChangeStateKey: String
```
```

The dictionary key for the skippable event state in the payload of the AVPlayerInterstitialEventMonitorCurrentEventSkippableStateDidChangeNotification.

Beta
```
```swift
```swift
```swift
let AVPlayerInterstitialEventMonitorCurrentEventSkippedEventKey: String
```
```

The dictionary key for the AVPlayerInterstitialEvent that was skipped in the payload of the AVPlayerInterstitialEventMonitorCurrentEventSkippedNotification.

Beta
```
```swift
```swift
```swift
let AVPlayerInterstitialEventMonitorInterstitialEventDidFinishDidPlayEntireEventKey: String
```
```

The dictionary key to indicate whether the event that finished playing was fully played out in the payload of the AVPlayerInterstitialEventMonitorInterstitialEventDidFinishNotification.

Beta
```
```swift
```swift
```swift
let AVPlayerInterstitialEventMonitorInterstitialEventDidFinishEventKey: String
```
```

The dictionary key for the AVPlayerInterstitialEvent that finished playing in the payload of the AVPlayerInterstitialEventMonitorInterstitialEventDidFinishNotification.

Beta
```
```swift
```swift
```swift
let AVPlayerInterstitialEventMonitorInterstitialEventDidFinishPlayoutTimeKey: String
```
```

The dictionary key for the playout time of the event that finished playing in the payload of the AVPlayerInterstitialEventMonitorInterstitialEventDidFinishNotification.

Beta
```
```swift
```swift
```swift
let AVPlayerInterstitialEventMonitorInterstitialEventWasUnscheduledErrorKey: String
```
```

The dictionary key to indicate whether the event that was unscheduled was due to an error.

Beta
```
```swift
```swift
```swift
let AVPlayerInterstitialEventMonitorInterstitialEventWasUnscheduledEventKey: String
```
```

The dictionary key for the AVPlayerInterstitialEvent that was unscheduled in the payload of the AVPlayerInterstitialEventMonitorInterstitialEventWasUnscheduledNotification.

Beta
```
```swift
```swift
```swift
let AVURLAssetShouldParseExternalSphericalTagsKey: String
```
```

Indicates whether additional projected media signaling in the asset should be parsed and resolved as format description extensions.

Beta
```
```

### [Type Aliases](/documentation/AVFoundation#Type-Aliases)

```swift
```swift
```swift
```swift
typealias AVURLAssetTrack
```
```
```
```

### [Enumerations](/documentation/AVFoundation#Enumerations)

```swift
```swift
```swift
```swift
enum AVCaptureCameraLensSmudgeDetectionStatus
```
```
Beta
```
```