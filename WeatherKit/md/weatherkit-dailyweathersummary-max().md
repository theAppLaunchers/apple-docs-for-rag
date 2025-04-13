

- WeatherKit
- DailyWeatherSummary
-  max() 

Instance Method

# max()

Returns the maximum element in the sequence.

WeatherKitSwiftiOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
@warn_unqualified_access
func max() -> Self.Element?
```

Available when `Element` conforms to `Comparable`.

## Return Value

The sequence’s maximum element. If the sequence has no elements, returns `nil`.

## Discussion

This example finds the largest value in an array of height measurements.

```
let heights = [67.5, 65.7, 64.3, 61.1, 58.5, 60.3, 64.9]
let greatestHeight = heights.max()
print(greatestHeight)
// Prints "Optional(67.5)"
```

Complexity

O(*n*), where *n* is the length of the sequence.

