

- RealityKit
- ActionAnimation
-  delay 

Instance Property

# delay

An amount of time that lapses before the animation plays.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
var delay: TimeInterval { get set }
```

## Discussion

The default value is `0`, which indicates that the animation plays with no delay. If you set a value for this property, the animation plays from its start time after the specified delay lapses.

During the delayed time, the animation doesn’t update. However, to fill the delayed time with some portion of animation, set a negative `AnimationAction/trimStart` instead and choose a `AnimationAction/fillMode` that displays the desired portion of animation.

