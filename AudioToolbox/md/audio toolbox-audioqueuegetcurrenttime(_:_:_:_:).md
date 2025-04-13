

- Audio Toolbox
-  AudioQueueGetCurrentTime(\_:\_:\_:\_:) 

Function

# AudioQueueGetCurrentTime(\_:\_:\_:\_:)

Gets the current audio queue time.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
func AudioQueueGetCurrentTime(
    _ inAQ: AudioQueueRef,
    _ inTimeline: AudioQueueTimelineRef?,
    _ outTimeStamp: UnsafeMutablePointer?,
    _ outTimelineDiscontinuity: UnsafeMutablePointer?
) -> OSStatus
```

## Parameters 

`inAQ`  

The audio queue whose current time you want to get.

`inTimeline`  

The audio queue timeline object to which timeline discontinuities are reported. Use `NULL` if the audio queue does not have an associated timeline object.

`outTimeStamp`  

On output, the current audio queue time. The `mSampleTime` field represents audio queue time in terms of the audio queue sample rate, relative to when the queue started or will start.

`outTimelineDiscontinuity`  

On output, `true` if there has been a timeline discontinuity, or `false` if there has been no discontinuity. If the audio queue does not have an associated timeline object, this parameter is always `NULL`.

A timeline discontinuity may occur, for example, if the sample rate is changed for the audio hardware device associated with an audio queue.

## Return Value

A result code. See Result Codes.

## See Also

### Managing the Timeline

func AudioQueueCreateTimeline(AudioQueueRef, UnsafeMutablePointer&lt;AudioQueueTimelineRef?>) -> OSStatus

Creates a timeline object for an audio queue.

func AudioQueueDisposeTimeline(AudioQueueRef, AudioQueueTimelineRef) -> OSStatus

Disposes of an audio queue’s timeline object.

func AudioQueueDeviceGetCurrentTime(AudioQueueRef, UnsafeMutablePointer&lt;AudioTimeStamp>) -> OSStatus

Gets the current time of the audio hardware device associated with an audio queue.

func AudioQueueDeviceGetNearestStartTime(AudioQueueRef, UnsafeMutablePointer&lt;AudioTimeStamp>, UInt32) -> OSStatus

Gets the start time, for an audio hardware device, that is closest to a requested start time.

func AudioQueueDeviceTranslateTime(AudioQueueRef, UnsafePointer&lt;AudioTimeStamp>, UnsafeMutablePointer&lt;AudioTimeStamp>) -> OSStatus

Converts the time for an audio queue’s associated audio hardware device from one time base representation to another.

typealias AudioQueueTimelineRef

Defines an opaque data type that represents an audio queue timeline object.

