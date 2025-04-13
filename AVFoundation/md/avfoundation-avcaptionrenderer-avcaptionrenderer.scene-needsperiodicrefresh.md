

- AVFoundation
- AVCaptionRenderer
- AVCaptionRenderer.Scene
-  needsPeriodicRefresh 

Instance Property

# needsPeriodicRefresh

A Boolean value that indicates whether the scene requires redrawing while your app progresses through the content.

iOS 18.0+iPadOS 18.0+Mac Catalyst 15.0+macOS 12.0+

``` source
var needsPeriodicRefresh: Bool { get }
```

## Discussion

If your app isn’t progressing through the content, a single render at the current time is enough.

Choose a refresh rate appropriate for your app. For example, an app may choose rates that match rates of associated video frames or other timing appropriate for the client.

## See Also

### Inspecting the Scene

var timeRange: CMTimeRange

The time range during which the system doesn’t modify the scene.

var hasActiveCaptions: Bool

A Boolean value that indicates whether the scene contains one or more active captions.

