

- SwiftUI
- EnvironmentValues
-  accessibilityDifferentiateWithoutColor 

Instance Property

# accessibilityDifferentiateWithoutColor

Whether the system preference for Differentiate without Color is enabled.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
var accessibilityDifferentiateWithoutColor: Bool { get }
```

## Discussion

If this is true, UI should not convey information using color alone and instead should use shapes or glyphs to convey information.

## See Also

### Managing color

func accessibilityIgnoresInvertColors(Bool) -> some View

Sets whether this view should ignore the system Smart Invert setting.

var accessibilityInvertColors: Bool

Whether the system preference for Invert Colors is enabled.

