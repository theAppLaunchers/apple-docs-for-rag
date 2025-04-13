

- Core Media
-  kCMSampleBufferConduitNotificationParameter_MinUpcomingOutputPTS 

Global Variable

# kCMSampleBufferConduitNotificationParameter_MinUpcomingOutputPTS

Specifies the minimum presentation timestamp of upcoming output samples (type `CFDictionary`).

iOS 4.3+iPadOS 4.3+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
let kCMSampleBufferConduitNotificationParameter_MinUpcomingOutputPTS: CFString
```

## Discussion

This key may be present in the `userInfo` dictionary for the kCMSampleBufferConduitNotification_UpcomingOutputPTSRangeChanged notification in cases where upcoming frames may have earlier timestamps than those previously provided. Its value is the `CFDictionary` representation of a `CMTime` object (see CMTimeMakeFromDictionary(_:)).

Either this key or kCMSampleBufferConduitNotificationParameter_MaxUpcomingOutputPTS may be omitted to leave the range open-ended.

## See Also

### Sample Buffer Conduit Notifications

let kCMSampleBufferConduitNotification_ResetOutput: CFString

Posted on a conduit of sample buffers to request invalidation of pending output data.

let kCMSampleBufferConduitNotification_InhibitOutputUntil: CFString

Posted on a conduit of sample buffers to announce a coming discontinuity.

let kCMSampleBufferConduitNotification_UpcomingOutputPTSRangeChanged: CFString

Posted on a conduit of video sample buffers to report information about the range of upcoming output presentation timestamps.

let kCMSampleBufferConduitNotificationParameter_UpcomingOutputPTSRangeMayOverlapQueuedOutputPTSRange: CFString

Indicates that the presentation timestamps of upcoming output samples may overlap those of samples queued for output (type `CFBoolean`).

let kCMSampleBufferConduitNotificationParameter_MaxUpcomingOutputPTS: CFString

Specifies the maximum presentation timestamp of upcoming output samples (type `CFDictionary`).

let kCMSampleBufferConduitNotificationParameter_ResumeTag: CFString

Specifies a tag to be attached to the first sample buffer following a discontinuity (type `CFNumber`).

