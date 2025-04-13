

- AVKit
- AVPlayerViewController
-  showsPlaybackControls 

Instance Property

# showsPlaybackControls

A Boolean value that indicates whether the player view controller shows playback controls.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
var showsPlaybackControls: Bool { get set }
```

## Discussion

Set this property to false if you don’t want the system-provided playback controls visible over your content. Hiding the playback controls can be useful in situations where you need a non-interactive video presentation, such as a video splash screen.

The default value is true.

Important

Don’t use this property to change the visibility of the playback controls while the player view controller is onscreen. Doing so creates or destroys user interface elements.

## See Also

### Configuring Presentation

var contentOverlayView: UIView?

A view that displays between the video content and the playback controls.

var videoGravity: AVLayerVideoGravity

A string that specifies how the video displays within the bounds of the view controller’s view.

var videoBounds: CGRect

The size and position of the video image within the bounds of the view controller’s view.

var showsTimecodes: Bool

A Boolean value that determines whether the player view displays timecodes, if available.

var appliesPreferredDisplayCriteriaAutomatically: Bool

A Boolean value that indicates whether the view controller automatically sets the screen’s display criteria to match that of the currently playing asset.

