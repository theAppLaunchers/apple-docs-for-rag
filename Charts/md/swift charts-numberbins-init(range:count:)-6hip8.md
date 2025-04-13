

- Swift Charts
- NumberBins
-  init(range:count:) 

Initializer

# init(range:count:)

Creates the given number of bins for the range. Expects that the range length is a multiple of `count` to allow uniform integer bins.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
nonisolated
init(
    range: ClosedRange,
    count: Int
) where Value : BinaryInteger
```

## Parameters 

`range`  

The range of the bins. The first bin starts at the lower bound of the range, and the last bin ends at the upper bound of the range.

`count`  

The exact number of bins.

