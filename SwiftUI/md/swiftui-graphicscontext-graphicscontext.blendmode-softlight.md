

- SwiftUI
- GraphicsContext
- GraphicsContext.BlendMode
-  softLight 

Type Property

# softLight

A mode that either darkens or lightens colors, depending on the source image sample color.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static var softLight: GraphicsContext.BlendMode { get }
```

## Discussion

If the source image sample color is lighter than 50% gray, the background is lightened, similar to dodging. If the source image sample color is darker than 50% gray, the background is darkened, similar to burning. If the source image sample color is equal to 50% gray, the background is not changed. Image samples that are equal to pure black or pure white produce darker or lighter areas, but do not result in pure black or white. The overall effect is similar to what you’d achieve by shining a diffuse spotlight on the source image. Use this to add highlights to a scene.

## See Also

### Adding contrast

static var overlay: GraphicsContext.BlendMode

A mode that either multiplies or screens the source image samples with the background image samples, depending on the background color.

static var hardLight: GraphicsContext.BlendMode

A mode that either multiplies or screens colors, depending on the source image sample color.

