

- Metal
- MTLSamplerDescriptor
-  maxAnisotropy 

Instance Property

# maxAnisotropy

The number of samples that can be taken to improve the quality of sample footprints that are anisotropic.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.11+tvOSvisionOS 1.0+

``` source
var maxAnisotropy: Int { get set }
```

## Discussion

Values must be between `1` and `16`, inclusive. The default value is `1`.

## See Also

### Declaring Filter Modes

var minFilter: MTLSamplerMinMagFilter

The filtering option for combining pixels within one mipmap level when the sample footprint is larger than a pixel (minification).

var magFilter: MTLSamplerMinMagFilter

The filtering operation for combining pixels within one mipmap level when the sample footprint is smaller than a pixel (magnification).

var mipFilter: MTLSamplerMipFilter

The filtering option for combining pixels between two mipmap levels.

var lodMinClamp: Float

The minimum level of detail (LOD) to use when sampling from a texture.

var lodMaxClamp: Float

The maximum level of detail (LOD) to use when sampling from a texture.

var lodAverage: Bool

A Boolean value that specifies whether the GPU can use an average level of detail (LOD) when sampling from a texture.

enum MTLSamplerMinMagFilter

Filtering options for determining which pixel value is returned within a mipmap level.

enum MTLSamplerMipFilter

Filtering options for determining what pixel value is returned with multiple mipmap levels.

