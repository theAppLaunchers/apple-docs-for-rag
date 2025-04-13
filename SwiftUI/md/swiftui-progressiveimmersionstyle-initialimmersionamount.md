

- SwiftUI
- ProgressiveImmersionStyle
-  initialImmersionAmount 

Instance Property

# initialImmersionAmount

The initial amount of immersion used for this instance of the style.

visionOS 2.0+

``` source
let initialImmersionAmount: Double?
```

## Discussion

The value represents how much of the spherical field of view of the user is covered by the portal effect of the style initially. The value can range from `0.0` to `1.0`, and is capped by the minimum and maximum amount of immersion of this instance. If this value is not set, a system default value will be used instead.

