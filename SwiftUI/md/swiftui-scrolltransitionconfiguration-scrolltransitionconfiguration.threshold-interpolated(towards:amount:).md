

- SwiftUI
- ScrollTransitionConfiguration
- ScrollTransitionConfiguration.Threshold
-  interpolated(towards:amount:) 

Instance Method

# interpolated(towards:amount:)

Creates a new threshold that combines this threshold value with another threshold, interpolated by the given amount.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
func interpolated(
    towards other: ScrollTransitionConfiguration.Threshold,
    amount: Double
) -> ScrollTransitionConfiguration.Threshold
```

## Parameters 

`other`  

The second threshold value.

`amount`  

The ratio with which this threshold is combined with the given threshold, where zero is equal to this threshold, 1.0 is equal to `other`, and values in between combine the two thresholds.

## See Also

### Modifying the threshold

func inset(by: Double) -> ScrollTransitionConfiguration.Threshold

Returns a threshold that is met when the target view is closer to the center of the container by `distance`. Use negative values to move the threshold away from the center.

