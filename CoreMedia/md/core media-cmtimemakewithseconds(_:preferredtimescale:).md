

- Core Media
-  CMTimeMakeWithSeconds(\_:preferredTimescale:) 

Function

# CMTimeMakeWithSeconds(\_:preferredTimescale:)

Creates a time that represents a number of seconds in a preferred timescale.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMTimeMakeWithSeconds(
    _ seconds: Float64,
    preferredTimescale: Int32
) -> CMTime
```

## Parameters 

`seconds`  

The number of seconds to represent.

`preferredTimescale`  

The preferred timescale of the time.

## Return Value

A time structure.

## Discussion

Specify a positive preferred timescale value, or the resulting time is invalid.

If you specify a value that causes an overflow, the system repeatedly halves the value until the overflow goes away or the timescale equals `1`. If the value still overflows at that point, the system sets the value to positive or negative infinity.

Query the hasBeenRounded property value to determine whether the value, when converted back to seconds, precisely matches the original seconds value.

## See Also

### Creating a Time

func CMTimeMake(value: Int64, timescale: Int32) -> CMTime

Creates a time with a value and timescale.

func CMTimeMakeWithEpoch(value: Int64, timescale: Int32, epoch: Int64) -> CMTime

Creates a time with a value, timescale, and epoch.

func CMTimeMakeFromDictionary(CFDictionary?) -> CMTime

Creates a time from a dictionary representation of its fields.

