

- Core Media
- CMTime
-  init(value:timescale:) 

Initializer

# init(value:timescale:)

Creates a time with a value and timescale.

iOS 4.0+iPadOS 4.0+Mac CatalystmacOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
init(
    value: CMTimeValue,
    timescale: CMTimeScale
)
```

## Parameters 

`value`  

An integer time value.

`timescale`  

An integer timescale value.

## See Also

### Creating a Time

init(value: CMTimeValue, timescale: CMTimeScale, flags: CMTimeFlags, epoch: CMTimeEpoch)

Creates a time with a value, timescale, flags, and epoch.

init(seconds: Double, preferredTimescale: CMTimeScale)

Creates a time that represents number of seconds in a preferred timescale.

init()

Creates a time with an invalid value.

