

- Compositor Services
- LayerRenderer
- LayerRenderer.Drawable
-  rasterizationRateMaps 

Instance Property

# rasterizationRateMaps

The rasterization rate maps to use when rendering the frame.

visionOS 1.0+

``` source
var rasterizationRateMaps: [any MTLRasterizationRateMap] { get }
```

## Discussion

Apply a rasterization rate map to your render descriptor when you set up your drawing environment. A rate map defines how the GPU scales different parts of the texture to fill the display. You use these rate maps to save time and render less important parts of your scene at lower resolutions. For example, the drawable includes a rasterization rate map to render the portions of the texture in someone’s peripheral vision at a lower resolution. Rasterization rate maps are available only when foveation is enabled.

## See Also

### Getting the rasterization rate map

var flippedRasterizationRateMaps: [any MTLRasterizationRateMap]

The rasterization rate maps that are flipped around the y-axis.

