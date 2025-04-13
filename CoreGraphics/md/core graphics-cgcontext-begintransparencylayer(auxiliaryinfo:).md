

- Core Graphics
- CGContext
-  beginTransparencyLayer(auxiliaryInfo:) 

Instance Method

# beginTransparencyLayer(auxiliaryInfo:)

Begins a transparency layer.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.3+tvOSvisionOS 1.0+watchOS 2.0+

``` source
func beginTransparencyLayer(auxiliaryInfo: CFDictionary?)
```

## Parameters 

`auxiliaryInfo`  

A dictionary that specifies any additional information, or `NULL`.

## Discussion

Until a corresponding call to endTransparencyLayer(), all subsequent drawing operations in the specified context are composited into a fully transparent backdrop (which is treated as a separate destination buffer from the context).

After a call to `CGContextEndTransparencyLayer`, the result is composited into the context using the global alpha and shadow state of the context. This operation respects the clipping region of the context.

After a call to this function, all of the parameters in the graphics state remain unchanged with the exception of the following:

- The global alpha is set to `1`.

- The shadow is turned off.

Ending the transparency layer restores these parameters to their previous values. Core Graphics maintains a transparency layer stack for each context, and transparency layers may be nested.

Tip

For best performance, make sure that you set the smallest possible clipping area for the objects in the transparency layer prior to calling `CGContextBeginTransparencyLayer`.

## See Also

### Working with Transparency Layers

func beginTransparencyLayer(in: CGRect, auxiliaryInfo: CFDictionary?)

Begins a transparency layer whose contents are bounded by the specified rectangle.

func endTransparencyLayer()

Ends a transparency layer.

