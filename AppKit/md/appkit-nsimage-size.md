

- AppKit
- NSImage
-  size 

Instance Property

# size

The size of the image.

macOS

``` source
var size: NSSize { get set }
```

## Discussion

Defaults to `{0.0, 0.0}` if no size has been set and the size cannot be determined from any of the receiver’s image representations. If the size of the image hasn’t already been set when an image representation is added, the size is taken from the image representation’s data. For EPS images, the size is taken from the image’s bounding box. For TIFF images, the size is taken from the `ImageLength` and `ImageWidth` attributes.

Changing the size of an `NSImage` after it has been used effectively resizes the image. Changing the size invalidates all its caches and frees them. When the image is next composited, the selected representation will draw itself in an offscreen window to recreate the cache.

## See Also

### Setting Attributes of Images

var isTemplate: Bool

A Boolean value that determines whether the image represents a template image.

var isTemplate: Bool

A Boolean value that determines whether the image represents a template image.

