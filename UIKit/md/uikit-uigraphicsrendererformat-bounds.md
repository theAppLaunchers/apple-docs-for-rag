

- UIKit
- UIGraphicsRendererFormat
-  bounds 

Instance Property

# bounds

The bounds of the graphics context.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
var bounds: CGRect { get }
```

## Discussion

This value represents the bounds of every Core Graphics context that the associated graphics renderer creates.

If the graphics renderer itself creates a format object, the bounds are set to those provided to the renderer as part of the initializer.

