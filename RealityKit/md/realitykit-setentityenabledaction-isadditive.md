

- RealityKit
- SetEntityEnabledAction
-  isAdditive 

Instance Property

# isAdditive

A Boolean value that determines whether this action additively blends with the prior stage.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
var isAdditive: Bool { get }
```

## Discussion

When `true`, the action’s animation output is relative to an absolute base value, and the animation system blends the result additively with the prior blend stage.

Apply actions additively by configuring them to produce animation offsets, such as delta values.

The default value is `false`.

