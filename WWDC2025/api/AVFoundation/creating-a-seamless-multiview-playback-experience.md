*   [AVFoundation](/documentation/avfoundation)
*   [Media playback](/documentation/avfoundation/media-playback)
*   Creating a seamless multiview playback experience Beta

Sample Code

# Creating a seamless multiview playback experience

Build advanced multiview playback experiences with the AVFoundation and AVRouting frameworks.

[Download](https://docs-assets.developer.apple.com/published/4c71acc26b70/CreatingASeamlessMultiviewPlaybackExperience.zip)

iOS 26.0+BetaiPadOS 26.0+BetatvOS 26.0+BetaXcode 26.0+Beta

## [Overview](/documentation/AVFoundation/creating-a-seamless-multiview-playback-experience#Overview)

Note

This sample code project is associated with WWDC25 session 302: [Create a seamless multiview playback experience](https://developer.apple.com/videos/play/wwdc2025/302).

### [Configure the sample code project](/documentation/AVFoundation/creating-a-seamless-multiview-playback-experience#Configure-the-sample-code-project)

To run this sample, you’ll need the following:

*   An iOS device with iOS 26 or later or
    
*   A tvOS device with tvOS 26 or later
    

## [See Also](/documentation/AVFoundation/creating-a-seamless-multiview-playback-experience#see-also)

### [Playback control](/documentation/AVFoundation/creating-a-seamless-multiview-playback-experience#Playback-control)

[

Observing playback state in SwiftUI](/documentation/avfoundation/observing-playback-state-in-swiftui)

Keep your user interface in sync with state changes from playback objects.

[

Controlling the transport behavior of a player](/documentation/avfoundation/controlling-the-transport-behavior-of-a-player)

Play, pause, and seek through a media presentation.

```swift
```swift
```swift
class AVPlayer
```
```

An object that provides the interface to control the player’s transport behavior.
```
```swift
```swift
```swift
class AVPlayerItem
```
```

An object that models the timing and presentation state of an asset during playback.
```
```swift
```swift
```swift
class AVPlayerItemTrack
```
```

An object that represents the presentation state of an asset track during playback.
```
```swift
```swift
```swift
class AVQueuePlayer
```
```

An object that plays a sequence of player items.
```
```swift
```swift
```swift
class AVPlayerLooper
```
```

An object that loops media content using a queue player.
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)