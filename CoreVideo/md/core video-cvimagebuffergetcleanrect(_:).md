

- Core Video
-  CVImageBufferGetCleanRect(\_:) 

Function

# CVImageBufferGetCleanRect(\_:)

Returns the source rectangle of a Core Video image buffer that represents the clean aperture of the buffer in encoded pixels.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.4+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CVImageBufferGetCleanRect(_ imageBuffer: CVImageBuffer) -> CGRect
```

## Parameters 

`imageBuffer`  

The image buffer containing the clean aperture to retrieve.

## Return Value

A CGRect structure returning the nominal display size of the image buffer. The size is zero if you pass a value for the image buffer that isn’t a CVImageBuffer type.

## Discussion

The clean aperture size is smaller than the full size of the image. For example, for an NTSC DV frame, this function returns a CGRect structure with an origin of `(8,0)` and a size of 704 x 480.

Note

The origin of this rectangle is always in the lower-left corner. This is the same coordinate system as that used by Quartz and Core Image.

## See Also

### Inspecting image buffers

func CVImageBufferGetColorSpace(CVImageBuffer) -> Unmanaged&lt;CGColorSpace>?

Returns the color space of a Core Video image buffer.

func CVImageBufferGetDisplaySize(CVImageBuffer) -> CGSize

Returns the nominal output display size, in square pixels, of a Core Video image buffer.

func CVImageBufferGetEncodedSize(CVImageBuffer) -> CGSize

Returns the full encoded dimensions of a Core Video image buffer.

func CVImageBufferIsFlipped(CVImageBuffer) -> Bool

Returns a Boolean value indicating whether the image is vertically flipped.

