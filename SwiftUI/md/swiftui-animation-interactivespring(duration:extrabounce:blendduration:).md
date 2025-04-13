

- SwiftUI
- Animation
-  interactiveSpring(duration:extraBounce:blendDuration:) 

Type Method

# interactiveSpring(duration:extraBounce:blendDuration:)

A convenience for a `spring` animation with a lower `response` value, intended for driving interactive animations.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
static func interactiveSpring(
    duration: TimeInterval = 0.15,
    extraBounce: Double = 0.0,
    blendDuration: TimeInterval = 0.25
) -> Animation
```

