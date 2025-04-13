

- SwiftUI
- ProgressiveImmersionStyle
-  minimumImmersionAmount 

Instance Property

# minimumImmersionAmount

The minimum amount of immersion used for this instance of the style.

visionOS 2.0+

``` source
let minimumImmersionAmount: Double?
```

## Discussion

The value represents the minimum amount of the spherical field of view of the user that can be covered by the portal effect of the style. The value can range from `0.0` to `1.0`. If this value is not set, a system default value will be used instead.

