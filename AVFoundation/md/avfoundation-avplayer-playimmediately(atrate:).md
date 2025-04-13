

- AVFoundation
- AVPlayer
-  playImmediately(atRate:) 

Instance Method

# playImmediately(atRate:)

Plays the available media data immediately, at the specified rate.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
nonisolated
func playImmediately(atRate rate: Float)
```

## Parameters 

`rate`  

The specified playback rate.

## Discussion

This method plays the available media data at the specified `rate` regardless of whether there is sufficient media buffered to ensure smooth playback. If media data exists in the playback buffer, calling this method changes the player’s playback rate to the specified `rate` and its timeControlStatus to a value of AVPlayer.TimeControlStatus.playing. If the player has insufficient media data buffered to begin playback, the player will behave as if it has encountered a stall during playback, except that no playbackStalledNotification will be posted.

## See Also

### Configuring Waiting Behavior

var automaticallyWaitsToMinimizeStalling: Bool

A Boolean value that indicates whether the player should automatically delay playback in order to minimize stalling.

var reasonForWaitingToPlay: AVPlayer.WaitingReason?

The reason the player is currently waiting for playback to begin or resume.

struct WaitingReason

The reasons a player is waiting to begin or resume playback.

var timeControlStatus: AVPlayer.TimeControlStatus

A value that indicates whether playback is in progress, paused indefinitely, or waiting for network conditions to improve.

enum TimeControlStatus

Constants that indicate the state of playback control.

