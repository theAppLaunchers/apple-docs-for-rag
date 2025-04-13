

- SwiftUI
- GraphicsContext
- GraphicsContext.Filter
-  blur(radius:options:) 

Type Method

# blur(radius:options:)

Returns a filter that applies a Gaussian blur.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static func blur(
    radius: CGFloat,
    options: GraphicsContext.BlurOptions = BlurOptions()
) -> GraphicsContext.Filter
```

## Parameters 

`radius`  

The standard deviation of the Gaussian blur.

`options`  

A set of options controlling the application of the effect.

## Return Value

A filter that applies Gaussian blur.

