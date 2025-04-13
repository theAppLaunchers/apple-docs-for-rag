

- RealityKit
- ARView
- ARView.PostProcessContext
-  init(\_:\_:\_:\_:\_:\_:\_:) 

Initializer

# init(\_:\_:\_:\_:\_:\_:\_:)

Creates a new context object.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
init(
    _ device: any MTLDevice,
    _ commandBuffer: any MTLCommandBuffer,
    _ sourceColorTexture: any MTLTexture,
    _ sourceDepthTexture: any MTLTexture,
    _ targetColorTexture: any MTLTexture,
    _ projection: float4x4,
    _ time: TimeInterval
)
```

## Parameters 

`device`  

The Metal device the view renders to.

`commandBuffer`  

The Metal command buffer that encodes this view.

`sourceColorTexture`  

A texture containing the rendered frame.

`sourceDepthTexture`  

A texture containing the frame’s depth buffer.

`targetColorTexture`  

A texture the callback function writes to.

`projection`  

The projection matrix for this frame.

`time`  

The current elapsed time.

## Discussion

This initializer creates a new postprocess context object. RealityKit creates context objects and passes them to the postprocess render callback. Your code won’t usually need to create context objects directly.

