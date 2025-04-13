

- Accelerate
- vImage
- vImage.PixelBuffer
-  withUnsafeRegionOfInterest(\_:\_:) 

Instance Method

# withUnsafeRegionOfInterest(\_:\_:)

Calls the given closure with a pixel buffer that references the image data within the specified region of interest.

iOS 16.0+iPadOS 16.0+Mac CatalystmacOS 13.0+tvOS 16.0+visionOSwatchOS 9.0+

``` source
func withUnsafeRegionOfInterest(
    _ regionOfInterest: CGRect,
    _ body: (vImage.PixelBuffer) throws -> R
) rethrows -> R
```

Available when `Format` conforms to `StaticPixelFormat`.

## Parameters 

`regionOfInterest`  

The region of interest.

`body`  

A closure with a vImage.PixelBuffer parameter that references the region of interest.

## Mentioned in 

Converting chroma-subsampled images

Applying vImage operations to regions of interest

## Discussion

Use this function to apply a vImage operation to a region of interest in a pixel buffer. This region of interest pixel buffer that this function passes to the closure as an argument references the same underlying memory as `self`. Therefore, changes the pixel buffer in the closure are changes in `self`.

For example, the following code generates a 5 x 5 pixel buffer filled with `1`s. The code applies a multiplication operation to a region of interest with the pixel buffer that mutplies each pixel by 5:

```
let src = vImage.PixelBuffer (
    pixelValues: [ 1, 1, 1, 1, 1,
                   1, 1, 1, 1, 1,
                   1, 1, 1, 1, 1,
                   1, 1, 1, 1, 1,
                   1, 1, 1, 1, 1 ],
    size: vImage.Size(width: 5,
                      height: 5))

let roi = CGRect(x: 1, y: 1,
                 width: 3, height: 3)

src.withUnsafeRegionOfInterest(roi) {
    roiPixelBuffer in

    roiPixelBuffer.multiply(by: 5,
                            divisor: 1,
                            preBias: 0, postBias: 0,
                            destination: roiPixelBuffer)
}

// Prints
// "[ 1, 1, 1, 1, 1,
//    1, 5, 5, 5, 1,
//    1, 5, 5, 5, 1,
//    1, 5, 5, 5, 1,
//    1, 1, 1, 1, 1 ]"
print(src.array)
```

To apply an operation that doesn’t work in place to a region of interest, create a temporary buffer to receive the result and call \`copy(to:)\` to write the result back to the region of interest buffer. For example, the following code applies a box blur to a centered rectangle within the source buffer:

```
let srcImage =  imageLiteral(resourceName: " ... ").cgImage(
    forProposedRect: nil,
    context: nil,
    hints: nil)!

var cgImageFormat = vImage_CGImageFormat(
    bitsPerComponent: 8,
    bitsPerPixel: 8 * 4,
    colorSpace: CGColorSpaceCreateDeviceRGB(),
    bitmapInfo: CGBitmapInfo(rawValue: CGImageAlphaInfo.noneSkipFirst.rawValue))!

let buffer = try vImage.PixelBuffer(
    cgImage: srcImage,
    cgImageFormat: &cgImageFormat,
    pixelFormat: vImage.Interleaved8x4.self)

let roi = CGRect(origin: .zero,
                 size: CGSize(width: buffer.width,
                              height: buffer.height)).insetBy(dx: 150,
                                                              dy: 150)

buffer.withUnsafeRegionOfInterest(roi) { buf in

    let tmp = vImage.PixelBuffer(
        size: vImage.Size(exactly: roi.size)!)

    buf.boxConvolve(kernelSize: vImage.Size(width: 17,
                                            height: 17),
                    edgeMode: .truncateKernel,
                    destination: tmp)

    tmp.copy(to: buf)
}
```

