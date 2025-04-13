

- Core Media
-  CMTimebaseSetRateAndAnchorTime(\_:rate:anchorTime:immediateSourceTime:) 

Function

# CMTimebaseSetRateAndAnchorTime(\_:rate:anchorTime:immediateSourceTime:)

Sets the time of a timebase at a particular host time, and changes the rate at exactly that time.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMTimebaseSetRateAndAnchorTime(
    _ timebase: CMTimebase,
    rate: Float64,
    anchorTime timebaseTime: CMTime,
    immediateSourceTime: CMTime
) -> OSStatus
```

## Discussion

The system interpolates `CMTimebaseGetTime`’s results from the anchor time as though the timebase has been running at the requested rate since that time.

`CMTimebaseSetRate(timebase, rate)` is approximately equivalent to calling `CMTimebaseSetRateAndAnchorTime(timebase, rate, CMTimebaseGetTime(timebase), CMSyncGetTime(CMTimebaseGetMaster(timebase)))`, except that `CMTimebaseSetRate` doesn’t generate a `TimeJumped` notification.

## See Also

### Getting and Setting the Time Rate

func CMTimebaseGetRate(CMTimebase) -> Float64

Returns the current rate of a timebase.

func CMTimebaseGetEffectiveRate(CMTimebase) -> Float64

Returns the effective rate of a timebase, which combines its rate with the rates of all its host timebases.

func CMTimebaseSetRate(CMTimebase, rate: Float64) -> OSStatus

Sets the rate of a timebase.

