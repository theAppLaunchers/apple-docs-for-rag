

- AppKit
- NSColor
-  init(name:dynamicProvider:) 

Initializer

# init(name:dynamicProvider:)

Creates a dynamic catalog color with a provider that’s used to resolve the exact color value, calculated on first use.

macOS 10.15+

``` source
init(
    name colorName: NSColor.Name?,
    dynamicProvider: @escaping (NSAppearance) -> NSColor
)
```

## Discussion

When methods on a color need color component values, AppKit calls the provider with currentDrawingAppearance. The provider can use the appearance to return another color to use for drawing. For example, if you create a color matching systemYellow for Light appearance, you’ll get a color matching systemYellow for Dark appearance when using Dark Mode. As often as possible, use the given appearance.

The `colorName` is equal to the identity of the color and should be universally unique; if `nil`, the system generates a unique name.

The name and the Light (aqua) appearance are encoded as part of this color. If a color is already registered with the same name as the decoded color, the decoded color joins the other color and becomes dynamic again.

