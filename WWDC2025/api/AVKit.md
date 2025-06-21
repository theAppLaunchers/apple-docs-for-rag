Framework

# AVKit

Create user interfaces for media playback, complete with transport controls, chapter navigation, picture-in-picture support, and display of subtitles and closed captions.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 9.0+

## [Topics](/documentation/AVKit#topics)

### [iOS playback and capture](/documentation/AVKit#iOS-playback-and-capture)

[

Playing video content in a standard user interface](/documentation/avkit/playing-video-content-in-a-standard-user-interface)

Play media full screen, embedded inline, or in a floating Picture in Picture (PiP) window using a player view controller.

```swift
```swift
```swift
class AVPlayerViewController
```
```

A view controller that displays content from a player and presents a native user interface to control playback.
```
```swift
```swift
```swift
protocol AVPlayerViewControllerDelegate
```
```

A protocol that defines the methods to implement to respond to player view controller events.
```
```swift
```swift
```swift
class AVCaptureEventInteraction
```
```

An object that registers handlers to respond to capture events from system hardware buttons.
```
```swift
```swift
```swift
class AVCaptureEvent
```
```

An object that describes a user interaction with a system hardware button.
```
```swift
```swift
```swift
class AVCaptureEventSound
```
```

A sound object for a capture event.

Beta
```
```swift
```swift
```swift
class AVInputPickerInteraction
```
```

Use `AVInputPickerInteraction` to present an input picker.

Beta
```

### [tvOS playback and capture](/documentation/AVKit#tvOS-playback-and-capture)

[

Customizing the tvOS Playback Experience](/documentation/avkit/customizing-the-tvos-playback-experience)

Adopt the latest features of the redesigned tvOS player user interface to provide a more streamlined way to watch your content.

[

Presenting Navigation Markers](/documentation/avkit/presenting-navigation-markers)

Present navigation markers in the Chapters panel to help users quickly navigate your content.

[

Working with Interstitial Content](/documentation/avkit/working-with-interstitial-content)

Present additional content alongside your main media presentation using HTTP Live Streaming support.

[

Presenting Content Proposals in tvOS](/documentation/avkit/presenting-content-proposals-in-tvos)

Display a preview of an upcoming media item at the conclusion of the currently playing media item.

[

Working with Overlays and Parental Controls in tvOS](/documentation/avkit/working-with-overlays-and-parental-controls-in-tvos)

Add interactive overlays, parental controls, and livestream channel flipping using a player view controller.

[

Supporting Continuity Camera in your tvOS app](/documentation/avkit/supporting-continuity-camera-in-your-tvos-app)

Capture high-quality photos, video, and audio in your Apple TV app by connecting an iPhone or iPad as a continuity device.

```swift
```swift
```swift
class AVPlayerViewController
```
```

A view controller that displays content from a player and presents a native user interface to control playback.
```
```swift
```swift
```swift
protocol AVPlayerViewControllerDelegate
```
```

A protocol that defines the methods to implement to respond to player view controller events.
```
```swift
```swift
```swift
class AVInterstitialTimeRange
```
```

A time range in an audiovisual presentation for content with an interstitial designation, such as advertisements or legal notices.
```
```swift
```swift
```swift
class AVNavigationMarkersGroup
```
```

A set of markers for navigating playback of an audiovisual presentation.
```
```swift
```swift
```swift
class AVContentProposalViewController
```
```

A view controller that proposes content to watch next.
```
```swift
```swift
```swift
class AVDisplayManager
```
```

A tvOS management object that controls whether a TV switches modes to match the video’s native mode.
```
```swift
```swift
```swift
class AVContinuityDevicePickerViewController
```
```

A view controller that provides an interface to a person so they can select and connect a continuity device to the system.
```
```swift
```swift
```swift
protocol AVContinuityDevicePickerViewControllerDelegate
```
```

An interface that responds to events from a continuity device picker view controller.
```

### [visionOS playback](/documentation/AVKit#visionOS-playback)

[

Playing immersive media with AVKit](/documentation/avkit/playing-immersive-media-with-avkit)

Adopt the system playback interface to provide an immersive video watching experience.

[

Creating a multiview video playback experience in visionOS](/documentation/avkit/creating-a-multiview-video-playback-experience-in-visionos)

Build an interface that plays multiple videos simultaneously and handles transitions to different experience types gracefully.

[

Adopting the system player interface in visionOS](/documentation/avkit/adopting-the-system-player-interface-in-visionos)

Provide an optimized viewing experience for watching 3D video content.

[

Trimming and exporting media in visionOS](/documentation/avkit/trimming-and-exporting-media-in-visionos)

Display standard controls in your app to edit the timeline of the currently playing media.

```swift
```swift
```swift
class AVPlayerViewController
```
```

A view controller that displays content from a player and presents a native user interface to control playback.
```
```swift
```swift
```swift
protocol AVPlayerViewControllerDelegate
```
```

A protocol that defines the methods to implement to respond to player view controller events.
```
```swift
```swift
```swift
class AVExperienceController
```
```

An object that controls video experiences.
```
```swift
```swift
```swift
class AVMultiviewManager
```
```

An object that manages viewing multiple videos at once.
```
```swift
```swift
```swift
class AVGroupExperienceCoordinator
```
```

An object that synchronizes viewing environment state across participants in a SharePlay session.
```

### [macOS playback and capture](/documentation/AVKit#macOS-playback-and-capture)

[

Implementing Trimming in a macOS Player](/documentation/avkit/implementing-trimming-in-a-macos-player)

Provide a QuickTime media-trimming experience in your macOS app.

```swift
```swift
```swift
class AVPlayerView
```
```

A view that displays content from a player and presents a native user interface to control playback.
```
```swift
```swift
```swift
class AVCaptureView
```
```

A view that displays standard user interface controls for capturing media data.
```

### [Multiplatform playback and capture](/documentation/AVKit#Multiplatform-playback-and-capture)

```swift
```swift
```swift
```swift
struct VideoPlayer
```
```

A view that displays content from a player and a native user interface to control playback.
```
```

### [Picture in Picture](/documentation/AVKit#Picture-in-Picture)

[

Adopting Picture in Picture Playback in tvOS](/documentation/avkit/adopting-picture-in-picture-playback-in-tvos)

Add advanced multitasking capabilities to your video apps by using Picture in Picture playback in tvOS.

[

Adopting Picture in Picture in a Standard Player](/documentation/avkit/adopting-picture-in-picture-in-a-standard-player)

Add Picture in Picture (PiP) playback to your app using a player view controller.

[

Adopting Picture in Picture in a Custom Player](/documentation/avkit/adopting-picture-in-picture-in-a-custom-player)

Add controls to your custom player user interface to invoke Picture in Picture (PiP) playback.

[

Adopting Picture in Picture for video calls](/documentation/avkit/adopting-picture-in-picture-for-video-calls)

Add multitasking capability to your video-call apps by using Picture in Picture (PiP).

[

Accessing the camera while multitasking on iPad](/documentation/avkit/accessing-the-camera-while-multitasking-on-ipad)

Operate the camera in Split View, Slide Over, Picture in Picture, and Stage Manager modes.

```swift
```swift
```swift
class AVPictureInPictureController
```
```

A controller that responds to user-initiated Picture in Picture playback of video in a floating, resizable window.
```

### [Playback route selection](/documentation/AVKit#Playback-route-selection)

```swift
```swift
```swift
```swift
class AVRoutePickerView
```
```

A view that presents a list of nearby media receivers.
```
```

### [Metadata](/documentation/AVKit#Metadata)

[

API Reference

AVKit Metadata Identifiers](/documentation/avkit/avkit-metadata-identifiers)

Additional metadata that an asset contains.

### [Errors](/documentation/AVKit#Errors)

```swift
```swift
```swift
```swift
let AVKitErrorDomain: String
```
```

The domain of errors the framework generates.
```
```swift
```swift
```swift
struct AVKitError
```
```

A structure that represents a framework error.
```
```swift
```swift
```swift
enum Code
```
```

Constants that identify framework error codes.
```
```

### [Macros](/documentation/AVKit#Macros)

[

API Reference

Macros](/documentation/avkit/avkit-macros)