

- AVFoundation
- AVDepthData
- AVDepthData.Accuracy
-  AVDepthData.Accuracy.relative 

Case

# AVDepthData.Accuracy.relative

Values within the depth data map are usable for foreground/background separation, but are not absolutely accurate in the physical world.

iOS 11.0+iPadOS 11.0+Mac Catalyst 14.0+macOS 10.13+tvOS 11.0+visionOS 1.0+

``` source
case relative
```

## Mentioned in 

Capturing Photos with Depth

## Discussion

This level of accuracy indicates that values within a depth map are usable relative to one another (that is, a depth value of 2 is twice as far as a depth value of 1), but do not accurately convey real-world distance.

## See Also

### Accuracy Values

case absolute

Values within the depth map are absolutely accurate within the physical world.

