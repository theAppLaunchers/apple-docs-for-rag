

- AppKit
- NSOpenGLPixelFormat
-  init(attributes:) Deprecated

Initializer

# init(attributes:)

Returns an OpenGL pixel format object initialized with specified pixel format attributes.

macOS 10.0–10.14Deprecated

``` source
convenience init?(attributes attribs: UnsafePointer)
```

Deprecated

Please use Metal or MetalKit.

## Parameters 

`attribs`  

A 0-terminated array containing Boolean and integer attribute constants. The presence of a Boolean attribute implies a value of true while its absence implies a value of false. Integer constants must be followed by the desired value. For a listing of attribute constants, see the constants in OpenGL Pixel Format Attributes.

## Return Value

An initialized `NSOpenGLPixelFormat` object whose attributes match the desired attributes as close as possible, or `nil` if an object with the desired attributes could not be initialized.

## Discussion

On return, the Boolean attributes of the receiver match the values specified in `attribs`, and the integer attributes are as close to the specified values as can be provided by the system.

The existence of a Boolean attribute constant in `attribs` implies a true value. The Boolean attribute constants are:

- `NSOpenGLPFAAllRenderers`

- `NSOpenGLPFADoubleBuffer`

- `NSOpenGLPFAStereo`

- `NSOpenGLPFAMinimumPolicy`

- `NSOpenGLPFAMaximumPolicy`

- `NSOpenGLPFAOffScreen`

- `NSOpenGLPFAFullScreen`

- `NSOpenGLPFASingleRenderer`

- `NSOpenGLPFANoRecovery`

- `NSOpenGLPFAAccelerated`

- `NSOpenGLPFAClosestPolicy`

- `NSOpenGLPFARobust`

- `NSOpenGLPFABackingStore`

- `NSOpenGLPFAWindow`

- `NSOpenGLPFAMultiScreen`

- `NSOpenGLPFACompliant`

- `NSOpenGLPFAPixelBuffer`

The integer constants must be followed by a value. These constants are:

- `NSOpenGLPFAAuxBuffers`

- `NSOpenGLPFAColorSize`

- `NSOpenGLPFAAlphaSize`

- `NSOpenGLPFADepthSize`

- `NSOpenGLPFAStencilSize`

- `NSOpenGLPFAAccumSize`

- `NSOpenGLPFARendererID`

- `NSOpenGLPFAScreenMask`

This code fragment creates a double-buffered pixel format with a 32-bit depth buffer:

```
NSOpenGLPixelFormatAttribute attrs[] =
{
    NSOpenGLPFADoubleBuffer,
    NSOpenGLPFADepthSize, 32,
    0
};

NSOpenGLPixelFormat* pixFmt = [[NSOpenGLPixelFormat alloc] initWithAttributes:attrs];

/* Check if initWithAttributes succeeded. */
if(pixFmt == nil) {
    /* initWithAttributes failed. Try to alloc/init with a different  list of attributes. */
}
```

## See Also

### Related Documentation

func getValues(UnsafeMutablePointer&lt;GLint>, forAttribute: NSOpenGLPixelFormatAttribute, forVirtualScreen: GLint)

Gets the value for the specified pixel format attribute.

Deprecated

### Creating an OpenGL Pixel Format

init?(cglPixelFormatObj: CGLPixelFormatObj)

Returns an OpenGL pixel format object initialized with using an existing CGL pixel format object.

Deprecated

