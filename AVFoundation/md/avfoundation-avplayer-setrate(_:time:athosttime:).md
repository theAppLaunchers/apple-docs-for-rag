

- AVFoundation
- AVPlayer
-  setRate(\_:time:atHostTime:) 

Instance Method

# setRate(\_:time:atHostTime:)

Synchronizes the playback rate and time of the current item with an external source.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 1.0+

``` source
nonisolated
func setRate(
    _ rate: Float,
    time itemTime: CMTime,
    atHostTime hostClockTime: CMTime
)
```

## Parameters 

`rate`  

The playback rate for the item.

`itemTime`  

The precise time at which to match playback of the item. To use the current item’s current time, specify invalid.

`hostClockTime`  

The host time at which to synchronize playback. If you specify invalid, the rate and time are set together without any external synchronization.

## Discussion

This method adjusts the current item’s timebase so that the time in `itemTime` is in sync with the time in `hostClockTime`. Thus, if `hostClockTime` specifies a time in the past, the item’s timebase is adjusted to make it appear as if the item has been running at the specified rate since `itemTime`. And if `hostClockTime` specifies a time in the future, playback is adjusted backward (if possible) so that the value in `itemTime` occurs at the precise moment the host’s clock reaches the value in `hostClockTime`. If there is no content to play before the time specified by `itemTime`, playback holds until the two times come into sync.

This method does not ensure that media data is loaded before the timebase starts moving. However, if you specify a host time in the near future, that would give you some time to load the media data and prepare for playback.

Important

This method is not currently supported for HTTP Live Streaming or when automaticallyWaitsToMinimizeStalling is true. For clients linked against iOS 10.0 and later or macOS 10.12 and later, invoking this method when automaticallyWaitsToMinimizeStalling is true will raise an `NSInvalidArgument` exception.

## See Also

### Synchronizing Multiple Players

func preroll(atRate: Float, completionHandler: ((Bool) -> Void)?)

Begins loading media data to prime the media pipelines for playback.

func cancelPendingPrerolls()

Cancels any pending preroll requests and invokes the corresponding completion handlers, if present.

var sourceClock: CMClock?

A clock the player uses for item time bases.

var masterClock: CMClock?

The host clock for item time bases.

Deprecated

