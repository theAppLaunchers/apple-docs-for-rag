

- Foundation
- NSNotification
- NSNotification.Name
-  AVSampleBufferAudioRendererOutputConfigurationDidChange 

Type Property

# AVSampleBufferAudioRendererOutputConfigurationDidChange

A notification the system posts to indicate that the hardware configuration doesn’t match the enqueued data format.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static let AVSampleBufferAudioRendererOutputConfigurationDidChange: NSNotification.Name
```

## Discussion

The output configuration of the playback hardware might change during the playback session if other apps play content in different formats. In these cases, the media content format doesn’t match the hardware configuration which would produce suboptimal rendering of the enqueued media data. When the framework detects such mismatch it posts this notification, so an app can flush the renderer and re-enqueue the sample buffers from the current media playhead, which configures the hardware based on the format of newly enqueued sample buffers.

## See Also

### AVFoundation

static let AVAssetChapterMetadataGroupsDidChange: NSNotification.Name

A notification the system posts when an asset’s chapter metadata groups change.

static let AVAssetContainsFragmentsDidChange: NSNotification.Name

A notification the system posts when an asset’s fragments change.

static let AVAssetDurationDidChange: NSNotification.Name

A notification the system posts when a fragmented asset minder observes a change to a fragmented asset’s duration.

static let AVAssetMediaSelectionGroupsDidChange: NSNotification.Name

A notification the system posts when an asset’s media selection groups change.

static let AVAssetTrackSegmentsDidChange: NSNotification.Name

A notification the system posts when a fragmented asset minder observes a change to a fragmented asset track’s segments.

static let AVAssetTrackTimeRangeDidChange: NSNotification.Name

A notification the system posts when a fragmented asset minder observes a change to a fragmented asset track’s time range.

static let AVAssetTrackTrackAssociationsDidChange: NSNotification.Name

A notification the system posts when the track associations for an asset track change.

static let AVAssetWasDefragmented: NSNotification.Name

A notification the system posts when a fragmented asset minder observes that the system defragments the asset on disk.

class let subjectAreaDidChangeNotification: NSNotification.Name

A notification the system posts when a capture device detects a substantial change to the video subject area.

class let wasConnectedNotification: NSNotification.Name

A notification the system posts when a new capture device becomes available.

class let wasDisconnectedNotification: NSNotification.Name

A notification the system posts when an existing device becomes unavailable.

class let formatDescriptionDidChangeNotification: NSNotification.Name

A notification the system posts when the capture input port’s format description changes.

class let didStartRunningNotification: NSNotification.Name

A notification the system posts when a capture session starts.

class let didStopRunningNotification: NSNotification.Name

A notification the system posts when a capture session stops.

class let interruptionEndedNotification: NSNotification.Name

A notification the system posts when an interruption to a capture session finishes.

