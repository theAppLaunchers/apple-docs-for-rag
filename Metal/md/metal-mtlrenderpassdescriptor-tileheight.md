

- Metal
- MTLRenderPassDescriptor
-  tileHeight 

Instance Property

# tileHeight

The tile height, in pixels.

iOS 11.0+iPadOS 11.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.5+visionOS 1.0+

``` source
var tileHeight: Int { get set }
```

## Discussion

The valid tile sizes are `32 x 32`, `32 x 16`, and `16 x 16`. If you do not set a tile size, the Metal device object chooses a default size.

## See Also

### Specifying Tile Shading Parameters

var imageblockSampleLength: Int

The per-sample size, in bytes, of the largest explicit imageblock layout in the render pass.

var threadgroupMemoryLength: Int

The per-tile size, in bytes, of the persistent threadgroup memory allocation.

var tileWidth: Int

The tile width, in pixels.

