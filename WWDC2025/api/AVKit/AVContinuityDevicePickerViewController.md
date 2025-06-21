*   [AVKit](/documentation/avkit)
*   AVContinuityDevicePickerViewController

Class

# AVContinuityDevicePickerViewController

A view controller that provides an interface to a person so they can select and connect a continuity device to the system.

tvOS 17.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
class AVContinuityDevicePickerViewController
```

```
```
```
```
```
```
```

## [Overview](/documentation/AVKit/AVContinuityDevicePickerViewController#overview)

The view controller presents an interface on an Apple TV that lets a person choose a nearby continuity device ([`AVContinuityDevice`](/documentation/AVFoundation/AVContinuityDevice)). Your app can then connect to that device’s cameras and microphones (see [`AVCaptureDevice`](/documentation/AVFoundation/AVCaptureDevice) and [`AVAudioSessionPortDescription`](/documentation/AVFAudio/AVAudioSessionPortDescription), respectively).

Important

The continuity device picker presents any devices near the Apple TV that use the same Apple ID.

To respond to the various outcome events from the picker, your app needs to implement the [`AVContinuityDevicePickerViewControllerDelegate`](/documentation/avkit/avcontinuitydevicepickerviewcontrollerdelegate) and assign it to the picker’s [`delegate`](/documentation/avkit/avcontinuitydevicepickerviewcontroller/delegate) property.

Note

SwiftUI apps can present the same interface with the [`continuityDevicePicker(isPresented:onDidConnect:)`](/documentation/SwiftUI/View/continuityDevicePicker\(isPresented:onDidConnect:\)) view modifier.

## [Topics](/documentation/AVKit/AVContinuityDevicePickerViewController#topics)

### [Checking for feature support](/documentation/AVKit/AVContinuityDevicePickerViewController#Checking-for-feature-support)

```swift
```swift
```swift
```swift
class var isSupported: Bool
```
```

A Boolean value that indicates whether the system supports connecting to a continuity device.
```
```

### [Designating a delegate](/documentation/AVKit/AVContinuityDevicePickerViewController#Designating-a-delegate)

```swift
```swift
```swift
```swift
var delegate: (any AVContinuityDevicePickerViewControllerDelegate)?
```
```

The delegate that responds to events from the continuity device picker view controller.
```
```

## [Relationships](/documentation/AVKit/AVContinuityDevicePickerViewController#relationships)

### [Inherits From](/documentation/AVKit/AVContinuityDevicePickerViewController#inherits-from)

*   [`UIViewController`](/documentation/UIKit/UIViewController)

### [Conforms To](/documentation/AVKit/AVContinuityDevicePickerViewController#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSExtensionRequestHandling`](/documentation/Foundation/NSExtensionRequestHandling)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`UIActivityItemsConfigurationProviding`](/documentation/UIKit/UIActivityItemsConfigurationProviding)
*   [`UIAppearanceContainer`](/documentation/UIKit/UIAppearanceContainer)
*   [`UIContentContainer`](/documentation/UIKit/UIContentContainer)
*   [`UIFocusEnvironment`](/documentation/UIKit/UIFocusEnvironment)
*   [`UIResponderStandardEditActions`](/documentation/UIKit/UIResponderStandardEditActions)
*   [`UIStateRestoring`](/documentation/UIKit/UIStateRestoring)
*   [`UITraitChangeObservable`](/documentation/UIKit/UITraitChangeObservable-67e94)
*   [`UITraitEnvironment`](/documentation/UIKit/UITraitEnvironment)
*   [`UIUserActivityRestoring`](/documentation/UIKit/UIUserActivityRestoring)

## [See Also](/documentation/AVKit/AVContinuityDevicePickerViewController#see-also)

### [tvOS playback and capture](/documentation/AVKit/AVContinuityDevicePickerViewController#tvOS-playback-and-capture)

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
protocol AVContinuityDevicePickerViewControllerDelegate
```
```

An interface that responds to events from a continuity device picker view controller.
```