

- Compositor Services
- LayerRenderer
- LayerRenderer.Capabilities
-  supportedDepthFormats 

Instance Property

# supportedDepthFormats

The list of depth formats that the layer supports

visionOS 1.0+

``` source
var supportedDepthFormats: [MTLPixelFormat] { get }
```

## Discussion

The pixel formats in this property tell you which pixel arrangements and characteristics the layer supports for its depth textures.

## See Also

### Getting the supported formats

var supportedColorFormats: [MTLPixelFormat]

An array of color formats that the layer supports for its textures.

