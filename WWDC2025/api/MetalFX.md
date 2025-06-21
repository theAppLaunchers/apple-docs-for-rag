Framework

# MetalFX

Boost your Metal app’s performance by upscaling lower-resolution content to save GPU time.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+

## [Overview](/documentation/MetalFX#overview)

The `MetalFX` framework integrates with [Metal](/documentation/Metal) to upscale a relatively low-resolution image to a higher output resolution in less time than it takes to render directly to the output resolution.

![A timeline diagram that compares a traditional rendering timespan and compares it to a MetalFX upscaling timespan. The MetalFX upscaling method, which renders at a lower resolution and then upscales to the final resolution with MetalFX, takes about half the time traditional rendering, which renders directly to the higher, final resolution.](https://docs-assets.developer.apple.com/published/d0d41d9865689f453bc27b90af756121/media-4085441%402x.png)

Use the GPU time savings to further enhance your app or game’s experience. For example, add more effects or scene details.

`MetalFX` gives you two different ways to upscale your input renderings:

*   Temporal antialiased upscaling
    
*   Spatial upscaling
    

If you can provide pixel color, depth, and motion information, add an [`MTLFXTemporalScaler`](/documentation/metalfx/mtlfxtemporalscaler) instance to your render pipeline. Otherwise, add an [`MTLFXSpatialScaler`](/documentation/metalfx/mtlfxspatialscaler) instance, which only requires a pixel color input texture.

Because the scaling effects take time to initialize, make an instance of either effect at launch or when a display changes resolutions. Once you’ve created an effect instance, you can use it repeatedly, typically once per frame.

## [Topics](/documentation/MetalFX#topics)

### [Temporal scaling](/documentation/MetalFX#Temporal-scaling)

[

Applying temporal antialiasing and upscaling using MetalFX](/documentation/metalfx/applying-temporal-antialiasing-and-upscaling-using-metalfx)

Reduce render workloads while increasing image detail with MetalFX.

```swift
```swift
```swift
protocol MTLFXTemporalScaler
```
```

An upscaling effect that generates a higher resolution texture in a render pass by analyzing multiple input textures over time.
```
```swift
```swift
```swift
class MTLFXTemporalScalerDescriptor
```
```

A set of properties that configure a temporal scaling effect, and a factory method that creates the effect.
```

### [Spatial scaling](/documentation/MetalFX#Spatial-scaling)

```swift
```swift
```swift
```swift
protocol MTLFXSpatialScaler
```
```

An upscaling effect that generates a higher resolution texture in a render pass by spatially analyzing an input texture.
```
```swift
```swift
```swift
class MTLFXSpatialScalerDescriptor
```
```

A set of properties that configure a spatial scaling effect, and a factory method that creates the effect.
```
```swift
```swift
```swift
enum MTLFXSpatialScalerColorProcessingMode
```
```

The color space modes for the input and output textures you use with a spatial scaling effect instance.
```
```

### [Classes](/documentation/MetalFX#Classes)

```swift
```swift
```swift
```swift
class MTLFXFrameInterpolatorDescriptor
```
```

A set of properties that configure a frame interpolator, and a factory method that creates the effect.

Beta
```
```swift
```swift
```swift
class MTLFXTemporalDenoisedScalerDescriptor
```
```
```
```

### [Protocols](/documentation/MetalFX#Protocols)

```swift
```swift
```swift
```swift
protocol MTL4FXFrameInterpolator
```
```
Beta
```
```swift
```swift
```swift
protocol MTL4FXSpatialScaler
```
```

An upscaling effect that generates a higher resolution texture in a render pass by spatially analyzing an input texture.

Beta
```
```swift
```swift
```swift
protocol MTL4FXTemporalDenoisedScaler
```
```
Beta
```
```swift
```swift
```swift
protocol MTL4FXTemporalScaler
```
```
Beta
```
```swift
```swift
```swift
protocol MTLFXFrameInterpolator
```
```
Beta
```
```swift
```swift
```swift
protocol MTLFXFrameInterpolatorBase
```
```

A common abstraction to all frame interpolators.
```
```swift
```swift
```swift
protocol MTLFXSpatialScalerBase
```
```

An upscaling effect that generates a higher resolution texture in a render pass by spatially analyzing an input texture.
```
```swift
```swift
```swift
protocol MTLFXTemporalDenoisedScaler
```
```
```
```swift
```swift
```swift
protocol MTLFXTemporalDenoisedScalerBase
```
```

A common abstraction to all denoiser scalers.
```
```swift
```swift
```swift
protocol MTLFXTemporalScalerBase
```
```

An upscaling effect that generates a higher resolution texture in a render pass by analyzing multiple input textures over time.
```
```