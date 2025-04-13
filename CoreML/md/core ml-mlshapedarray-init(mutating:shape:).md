

- Core ML
- MLShapedArray
-  init(mutating:shape:) 

Initializer

# init(mutating:shape:)

Creates a new `MLShapedArray` using a pixel buffer as the backing storage.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 1.0+watchOS 11.0+

``` source
init(
    mutating pixelBuffer: CVPixelBuffer,
    shape: [Int]
)
```

## Parameters 

`pixelBuffer`  

The backing pixel buffer. It must be backed by `IOSurface`.

`shape`  

The shape of the MLShapedArray. The last dimension of `shape` must match the pixel buffer’s width. The product of the rest of the dimensions must match the height.

## Discussion

Use this initializer to create an `IOSurface` backed `MLShapedArray`, which can reduce the inference latency by avoiding the buffer copy.

The pixel buffer’s pixel format type must be `OneComponent16Half`. As such, the scalar type must be `Float16`.

```
var pixelBuffer: CVPixelBuffer?
let pixelBufferAttributes = [
    kCVPixelBufferIOSurfacePropertiesKey : [:]
]
// Pixel buffer's width is the last dimension of `shape`, which is 4.
// The height is the product of the rest of the dimensions, which is
// 2 * 3 = 6.
CVPixelBufferCreate(kCFAllocatorDefault,
                    4, 6,
                    kCVPixelFormatType_OneComponent16Half,
                    pixelBufferAttributes as CFDictionary,
                    &pixelBuffer)

let shapedArray = MLShapedArray(mutating: pixelBuffer!,
                                         shape: [2, 3, 4])
```

When there is one and only one owner of the shaped array, mutating operations modifies the underlying pixel buffer.

```
var shapedArray = MLShapedArray(mutating: pixelBuffer, shape: [1])
shapedArray[scalarAt: 0] = 42
// The pixel buffer now has 42 in its frame buffer.
```

It follows the value semantics. The mutation doesn’t affect the copy.

```
var array1 = MLShapedArray(mutating: pixelBuffer, shape: [1])
array1[scalarAt: 0] = 0 // pixelBuffer is mutated.
let array2 = array1
array1[scalarAt: 0] = 42 // Copy-on-Write

assert(array1[scalarAt: 0] == 42)
assert(array2[scalarAt: 0] == 0)
```

It is undefined behavior to mutate the pixel buffer directly without using `.withMutablePixelBufferIfAvailable`.

