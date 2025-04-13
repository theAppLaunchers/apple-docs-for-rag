

- RealityKit
- LowLevelTexture
- LowLevelTexture.Descriptor
-  init(textureType:pixelFormat:width:height:depth:mipmapLevelCount:arrayLength:textureUsage:swizzle:) 

Initializer

# init(textureType:pixelFormat:width:height:depth:mipmapLevelCount:arrayLength:textureUsage:swizzle:)

Creates a descriptor for a low-level texture.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
init(
    textureType: MTLTextureType = .type2D,
    pixelFormat: MTLPixelFormat = .invalid,
    width: Int = 0,
    height: Int = 0,
    depth: Int = 1,
    mipmapLevelCount: Int = 1,
    arrayLength: Int = 1,
    textureUsage: MTLTextureUsage = .unknown,
    swizzle: MTLTextureSwizzleChannels = .init(red: .red, green: .green, blue: .blue, alpha: .alpha)
)
```

## Discussion

To create a new LowLevelTexture, first create a `LowLevelTexture.Descriptor` object and set its property values. Then, call init(descriptor:).

