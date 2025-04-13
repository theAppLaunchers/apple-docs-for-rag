

- Accelerate
- vImage
- vImage.PixelBuffer
-  planarBuffers() 

Instance Method

# planarBuffers()

Returns four 8-bit planar pixel buffers that contain the deinterleaved channels of the buffer.

iOS 16.0+iPadOS 16.0+Mac CatalystmacOS 13.0+tvOS 16.0+visionOSwatchOS 9.0+

``` source
func planarBuffers() -> [vImage.PixelBuffer]
```

Available when `Format` is `vImage.Interleaved8x4`.

## Return Value

An array of planar pixel buffers.

## Discussion

Use this function to deinterleave a buffer and create four new planar buffers that contain copies of each source channel. For example, the following code generates four 1 x 1 planar buffers from an vImage.Interleaved8x4 pixel buffer:

```
let src = vImage.PixelBuffer(
    pixelValues: [50, 100, 150, 200] as [UInt8],
    size: vImage.Size(width: 1, height: 1))

let planarBuffers: [vImage.PixelBuffer] = src.planarBuffers()

// Prints "[50] [100] [150] [200]"
for planarBuffer in planarBuffers {
    print(planarBuffer.array)
}
```

## See Also

### Generating planar buffers from interleaved buffers

func planarBuffers() -> [vImage.PixelBuffer&lt;vImage.Planar8>]

Returns two 8-bit planar pixel buffers that contain the deinterleaved channels of the buffer.

func planarBuffers() -> [vImage.PixelBuffer&lt;vImage.Planar8>]

Returns three 8-bit planar pixel buffers that contain the deinterleaved channels of the buffer.

func planarBuffers() -> [vImage.PixelBuffer&lt;vImage.PlanarF>]

Returns four 32-bit planar pixel buffers that contain the deinterleaved channels of the 8-bit buffer.

func planarBuffers() -> [vImage.PixelBuffer&lt;vImage.Planar16U>]

Returns four unsigned 16-bit planar pixel buffers that contain the deinterleaved channels of the buffer.

func planarBuffers() -> [vImage.PixelBuffer&lt;vImage.PlanarF>]

Returns two 32-bit planar pixel buffers that contain the deinterleaved channels of the buffer.

func planarBuffers() -> [vImage.PixelBuffer&lt;vImage.PlanarF>]

Returns three 32-bit planar pixel buffers that contain the deinterleaved channels of the buffer.

func planarBuffers() -> [vImage.PixelBuffer&lt;vImage.Planar8>]

Returns four 8-bit planar pixel buffers that contain the deinterleaved channels of the 32-bit buffer.

func planarBuffers() -> [vImage.PixelBuffer&lt;vImage.PlanarF>]

Returns four 32-bit planar pixel buffers that contain the deinterleaved channels of the buffer.

