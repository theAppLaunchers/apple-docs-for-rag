

- SwiftUI
- SymbolRenderingMode
-  monochrome 

Type Property

# monochrome

A mode that renders symbols as a single layer filled with the foreground style.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static let monochrome: SymbolRenderingMode
```

## Discussion

For example, you can render a filled exclamation mark triangle in purple:

```
Image(systemName: "exclamationmark.triangle.fill")
    .symbolRenderingMode(.monochrome)
    .foregroundStyle(Color.purple)
```

## See Also

### Getting symbol rendering modes

static let hierarchical: SymbolRenderingMode

A mode that renders symbols as multiple layers, with different opacities applied to the foreground style.

static let multicolor: SymbolRenderingMode

A mode that renders symbols as multiple layers with their inherit styles.

static let palette: SymbolRenderingMode

A mode that renders symbols as multiple layers, with different styles applied to the layers.

