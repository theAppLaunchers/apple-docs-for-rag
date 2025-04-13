

- Video Toolbox
-  kVTVideoDecoderSpecification_RequireHardwareAcceleratedVideoDecoder 

Global Variable

# kVTVideoDecoderSpecification_RequireHardwareAcceleratedVideoDecoder

A Boolean value indicating whether to require hardware-accelerated decoding.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 10.9+tvOS 17.0+visionOS 1.0+

``` source
let kVTVideoDecoderSpecification_RequireHardwareAcceleratedVideoDecoder: CFString
```

## Discussion

This key is set in the `decoderSpecification` passed in to VTDecompressionSessionCreate(allocator:formatDescription:decoderSpecification:imageBufferAttributes:outputCallback:decompressionSessionOut:). If set to kCFBooleanTrue, VideoToolbox tries to allocate a hardware-accelerated decoder. If it cannot, it returns an error and the session creation fails.

Setting this key automatically implies kVTVideoDecoderSpecification_EnableHardwareAcceleratedVideoDecoder–there is no need to set both and the Enable key does nothing if the Require key is set. This key is useful for clients that have their own software decoding implementation or those that may want to configure software and hardware decode sessions differently.

Hardware acceleration may be unavailable for a number of reasons:

- The machine doesn’t have hardware acceleration capabilities.

- The requested decoding format or configuration isn’t supported.

- The hardware decoding resources on the machine are busy.

## See Also

### Hardware Acceleration

let kVTVideoDecoderSpecification_EnableHardwareAcceleratedVideoDecoder: CFString

A Boolean value indicating whether VideoToolbox uses a hardware-accelerated video decoder, if available.

let kVTDecompressionPropertyKey_UsingHardwareAcceleratedVideoDecoder: CFString

Indicates if a hardware-accelerated video decoder is being used.

