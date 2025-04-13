

- SwiftUI
- GraphicsContext
- GraphicsContext.BlendMode
-  screen 

Type Property

# screen

A mode that multiplies the inverse of the source image samples with the inverse of the background image samples.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static var screen: GraphicsContext.BlendMode { get }
```

## Discussion

Drawing in this mode results in colors that are at least as light as either of the two contributing sample colors.

## See Also

### Lightening

static var lighten: GraphicsContext.BlendMode

A mode that creates composite image samples by choosing the lighter samples from either the source image or the background.

static var colorDodge: GraphicsContext.BlendMode

A mode that brightens the background image samples to reflect the source image samples.

static var plusLighter: GraphicsContext.BlendMode

A mode that adds the components of the source and background images, resulting in a lightened composite.

