

- RealityKit
- AnimationHandoffType
-  compose 

Type Property

# compose

Adds the new animation to existing animations, and immediately starts the new animation.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
static var compose: AnimationHandoffType { get }
```

## Discussion

Use this handoff for additive animations. If the new animation isn’t additive, then `compose` adds the new animation and removes the existing animation.

