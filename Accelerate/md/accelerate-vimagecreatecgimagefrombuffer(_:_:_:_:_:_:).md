

- Accelerate
-  vImageCreateCGImageFromBuffer(\_:\_:\_:\_:\_:\_:) 

Function

# vImageCreateCGImageFromBuffer(\_:\_:\_:\_:\_:\_:)

Creates a Core Graphics image from a vImage buffer.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 7.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageCreateCGImageFromBuffer(
    _ buf: UnsafePointer,
    _ format: UnsafePointer,
    _ callback: ((UnsafeMutableRawPointer?, UnsafeMutableRawPointer?) -> Void)!,
    _ userData: UnsafeMutableRawPointer!,
    _ flags: vImage_Flags,
    _ error: UnsafeMutablePointer!
) -> Unmanaged!
```

## Parameters 

`buf`  

The source vImage buffer.

`format`  

The image format of the source vImage buffer. If the format’s color space is `nil`, the function uses sRGB. The new Core Graphics image retains the color space.

`callback`  

A callback function that deallocates the source buffer’s data when the returned image no longer needs it. Pass this callback when you call this function in no-copy mode; that is, when you pass kvImageNoAllocate to `flags`. The system may call this function at any time — including before vImageCreateCGImageFromBuffer(_:_:_:_:_:_:) returns — and from any thread.

`userData`  

The value that passes to the `callback` function’s `userData` parameter.

`flags`  

The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

Pass kvImageNoAllocate to specify that the function runs in no-copy mode. In this case, the function passes the ownership of the source vImage buffer’s memory to the returned CGImage instance. When you pass this flag, specify the callback function to manage the deallocation of the memory.

Pass kvImageHighQualityResampling to specify high-quality resampling if the function resamples the output image to a smaller size.

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## Discussion

The following code shows a passthrough function that generates an output Core Graphics image using no-copy mode. The vImage buffer, `buffer`, and the Core Graphics image, `destinationCGImage`, share the same memory. In this example, the deallocation callback deallocates the memory that the `data` variable points to:

```
static func passThrough(sourceImage: CGImage) throws -> CGImage? {

    let alignmentAndRowBytes = try vImage_Buffer.preferredAlignmentAndRowBytes(
        width: sourceImage.width,
        height: sourceImage.height,
        bitsPerPixel: UInt32(sourceImage.bitsPerPixel))

    let data = UnsafeMutableRawPointer.allocate(
        byteCount: alignmentAndRowBytes.rowBytes * alignmentAndRowBytes.rowBytes,
        alignment: alignmentAndRowBytes.alignment)

    var buffer = vImage_Buffer(
        data: data,
        height: vImagePixelCount(sourceImage.height),
        width: vImagePixelCount(sourceImage.width),
        rowBytes: alignmentAndRowBytes.rowBytes)

    var format = vImage_CGImageFormat()

    vImageBuffer_InitWithCGImage(
        &buffer,
        &format,
        nil,
        sourceImage,
        vImage_Flags(kvImageNoAllocate))

    func callback(_: UnsafeMutableRawPointer?,
                  bufferData: UnsafeMutableRawPointer?) {
        bufferData?.deallocate()
    }

    let destinationCGImage = vImageCreateCGImageFromBuffer(
        &buffer,
        &format,
        callback,
        nil,
        vImage_Flags(kvImageNoAllocate),
        nil)

    return destinationCGImage?.takeRetainedValue()
}
```

