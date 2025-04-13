

- SwiftUI
- GraphicsContext
-  opacity 

Instance Property

# opacity

The opacity of drawing operations in the context.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var opacity: Double { get set }
```

## Discussion

Set this value to affect the opacity of content that you subsequently draw into the context. Changing this value has no impact on the content you previously drew into the context.

## See Also

### Setting opacity and the blend mode

var blendMode: GraphicsContext.BlendMode

The blend mode used by drawing operations in the context.

struct BlendMode

The ways that a graphics context combines new content with background content.

