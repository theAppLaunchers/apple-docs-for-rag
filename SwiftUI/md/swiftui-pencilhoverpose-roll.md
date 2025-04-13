

- SwiftUI
- PencilHoverPose
-  roll 

Instance Property

# roll

A value that represents the barrel roll angle of the hovering Apple Pencil.

iOS 17.5+iPadOS 17.5+Mac Catalyst 17.5+macOS 14.5+

``` source
let roll: Angle
```

## Discussion

This value is `.zero` when the user starts using their Apple Pencil, and changes relative to that initial angle as the user rolls the Apple Pencil alongside its barrel. If the Apple Pencil doesn’t support detecting its barrel roll angle, this property is always `.zero`.

