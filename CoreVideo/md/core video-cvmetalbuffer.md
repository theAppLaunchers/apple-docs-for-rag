

- Core Video
-  CVMetalBuffer 

Type Alias

# CVMetalBuffer

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.0+macOS 10.4+tvOS 9.0+visionOS 1.0+

``` source
typealias CVMetalBuffer = CVBuffer
```

## Discussion

```
@typedef    CVMetalBufferRef
@abstract   Metal buffer based CVPixelBuffer wrapped buffer
@discussion IMPORTANT NOTE: Clients should retain CVMetalBuffer objects until they are done using the contents in them.
            Retaining a CVMetalBuffer is your way to indicate that you're still using the image in the buffer, and that it should not be recycled yet.
```

