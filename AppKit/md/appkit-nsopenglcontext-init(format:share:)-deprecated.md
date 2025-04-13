

- AppKit
- NSOpenGLContext
-  init(format:share:) Deprecated

Initializer

# init(format:share:)

Returns an OpenGL context object initialized with the specified pixel format information.

macOS 10.0–10.14Deprecated

``` source
init?(
    format: NSOpenGLPixelFormat,
    share: NSOpenGLContext?
)
```

Deprecated

Please use Metal or MetalKit.

## Parameters 

`format`  

The pixel format to request for the OpenGL graphics context.

`share`  

Another OpenGL graphics context whose texture namespace and display lists you want to share with the receiver. If you do not want to share those features with another graphics context, you may pass `nil` for this parameter.

## Return Value

An `NSOpenGLContext` object initialized with the specified parameters, or `nil` if the object could not be created.

## Discussion

If the parameters contain invalid information, this method returns `nil`. This may happen if one of the following situations occurs:

- The `format` parameter is `nil` or contains an invalid pixel format.

- The `share` parameter is not `nil` and contains an invalid context.

- The `share` parameter contains a context with a pixel format that is incompatible with the one in `format`.

Pixel formats are incompatible if they use different renderers; this can happen if, for example, one format required an accumulation buffer that could only be provided by the software renderer, and the other format did not.

## See Also

### Related Documentation

Cocoa Drawing Guide

### Creating Contexts

init?(cglContextObj: CGLContextObj)

Initializes and returns an OpenGL context object using an existing CGL context.

Deprecated

