

- RealityKit
- ActionAnimation
-  speed 

Instance Property

# speed

A factor that changes the animation’s rate of playback.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
var speed: Float { get set }
```

## Discussion

The default value is `1.0`, which doesn’t alter the animation’s duration. A value of `2.0` indicates that the duration is half the normal rate. A value of `0.5` indicates that the duration is twice the normal rate. Negative values play the animation in reverse.

This property doesn’t affect the animation’s delay.

