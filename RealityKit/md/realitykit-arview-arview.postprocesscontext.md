

- RealityKit
- ARView
-  ARView.PostProcessContext 

Structure

# ARView.PostProcessContext

An object the framework uses to pass data to a postprocess callback.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
struct PostProcessContext
```

## Mentioned in 

Using Metal performance shaders to create custom postprocess effects

Implementing postprocess effects using Metal compute functions

Checking the pixel format of a postprocess effect’s output texture

## Overview

In iOS 15 and later, as well as macOS 12 and later, you can register a callback function to apply postprocessing effects to RealityKit’s rendered scene. Once every frame, RealityKit calls that function before it displays the scene. You can use this callback to apply postprocess effects using any APIs that can modify an image texture. However, because RealityKit calls this method every frame, you should only use APIs that execute on the GPU, such as Metal compute functions, Metal Performance Shaders, or Core Image. You can also render additional content, such as a rendered SpriteKit scene, on top of the frame buffer.

Note

For more information on implementing postprocess effects, see Implementing Special Rendering Effects with RealityKit Postprocessing, which demonstrates multiple postprocess techniques.

A postprocess callback takes a single `PostProcessContext` parameter, which contains data the callback function needs to modify the rendered scene, including the frame buffer, depth map, and a property for writing the modified image. If you’ve registered a postprocess callback, that function needs to encode to the output texture or the frame is never displayed.

A postprocess function looks like this:

```
    func myPostProcessCallback(context: ARView.PostProcessContext) {
        // Handle postprocessing here.
    }
```

To register a function as the postprocess render callback, assign it to the postProcess property of the renderCallbacks property of the scene’s `ARView`:

```
arView.renderCallbacks.postProcess = myPostProcessCallback
```

To stop postprocessing, set the postProcess render callback to `nil`.

```
arView.renderCallbacks.postProcess = nil
```

If your app turns postprocessing on and off frequently, another option for disabling postprocess effects is to keep your callback registered, but use an MTLBlitCommandEncoder to encode the unmodified framebuffer directly to the output texture whenever postprocess effects aren’t active.

```
 func myPostProcessCallback(context: ARView.PostProcessContext) {
     if (usePostProcessEffects) {
         handlePostProcessing(context: ARView.PostProcessContext)
         return
     }

     // If postprocess effects are disabled, copy sourceColorTexture
     // directly to targetColorTexture.
     let blitEncoder = context.commandBuffer.makeBlitCommandEncoder()
     blitEncoder?.copy(from: context.sourceColorTexture, to: context.targetColorTexture)
     blitEncoder?.endEncoding()
 }
```

## Topics

### Initializers

init(any MTLDevice, any MTLCommandBuffer, any MTLTexture, any MTLTexture, any MTLTexture, float4x4, TimeInterval)

Creates a new context object.

### Instance Properties

var commandBuffer: any MTLCommandBuffer

The Metal command buffer for encoding the frame.

var device: any MTLDevice

The Metal device where the scene renders.

var projection: float4x4

The projection matrix used to render the frame.

var sourceColorTexture: any MTLTexture

The rendered frame buffer.

var sourceDepthTexture: any MTLTexture

The frame’s depth buffer.

var targetColorTexture: any MTLTexture

The output texture where the postprocess callback writes the modified frame buffer.

var time: TimeInterval

The scene’s elapsed time.

## See Also

### Postprocessing

Postprocessing effects

Create special rendering effects for your RealityKit scenes.

struct RenderCallbacks

A container that holds the view’s render callbacks.

