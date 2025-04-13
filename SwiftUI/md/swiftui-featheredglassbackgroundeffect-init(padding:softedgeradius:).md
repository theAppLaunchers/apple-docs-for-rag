

- SwiftUI
- FeatheredGlassBackgroundEffect
-  init(padding:softEdgeRadius:) 

Initializer

# init(padding:softEdgeRadius:)

Creates a feathered glassBackground effect.

visionOS 2.4+

``` source
init(
    padding length: CGFloat,
    softEdgeRadius: CGFloat? = nil
)
```

## Return Value

A feathered background effect.

## Discussion

- padding: An amount, given in points, to pad all edges when style is renderding. However, it does not affect layout size, which is based on the content size. When it is less than effect’s blur size, the blur will be clipped.

- softEdgeRadius: When a blur is clipped, the radial size of the blur’s edge. If you set the value to `nil`, SwiftUI uses a default amount. The default value of this parameter is `nil`.

