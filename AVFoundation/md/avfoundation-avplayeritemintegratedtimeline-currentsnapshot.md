

- AVFoundation
- AVPlayerItemIntegratedTimeline
-  currentSnapshot 

Instance Property

# currentSnapshot

An immutable representation of the timeline state at time of request.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
var currentSnapshot: AVPlayerItemIntegratedTimelineSnapshot { get }
```

## Discussion

A timeline snapshot provides a read-only view of the details of the timeline. Because a snapshot provides a fixed view of the timeline at the time of the request, its state doesn’t update as playback continues.

## See Also

### Inspecting snapshots

class AVPlayerItemIntegratedTimelineSnapshot

An immutable representation of inspectable details of an integrated timeline object.

class let snapshotsOutOfSyncNotification: NSNotification.Name

A notification the system posts when the snapshot objects provided by this timeline become out of sync with the current timeline state.

