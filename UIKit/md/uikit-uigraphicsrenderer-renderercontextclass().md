

- UIKit
- UIGraphicsRenderer
-  rendererContextClass() 

Type Method

# rendererContextClass()

Specifies the drawing context class used by this graphics renderer.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
class func rendererContextClass() -> AnyClass
```

## Return Value

A subclass of UIGraphicsRendererContext suitable for the current renderer.

## Discussion

Each subclass of `UIGraphicsRenderer` can define its own subclass of UIGraphicsRendererContext. The graphics renderer calls this method whenever it needs to create a new graphics renderer context.

Override this method to specify the context class that the graphics renderer should use.

## See Also

### Managing graphics contexts

class func context(with: UIGraphicsRendererFormat) -> CGContext?

Creates a Core Graphics context configured according to the supplied format object.

class func prepare(CGContext, with: UIGraphicsRendererContext)

Applies the configuration specified in the renderer context to the Core Graphics context.

