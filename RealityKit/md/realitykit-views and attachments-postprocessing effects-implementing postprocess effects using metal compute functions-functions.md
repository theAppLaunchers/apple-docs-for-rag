

- RealityKit
- Views and attachments
- Postprocessing effects
-  Implementing postprocess effects using Metal compute functions 

Article

# Implementing postprocess effects using Metal compute functions

Create custom shaders to implement postprocess effects.

## Overview

In iOS 15 and later, and macOS 12 and later, you can apply postprocess effects to a RealityKit scene after RealityKit renders it, but before RealityKit displays it. If you register a postprocess callback function, RealityKit passes that function the complete, rendered frame so you can modify it before the viewer sees it. You can use any image-processing or drawing APIs on the rendered frame but, as a practical matter, only APIs that execute on the GPU are fast enough to use every frame and maintain a good framerate.

One way to implement postprocess effects is to write custom Metal compute functions to process the rendered scene. Writing your own custom compute function gives you tremendous flexibility and allows you to create virtually any postprocessing effect. Because compute functions run on the GPU, they’re a good choice for implementing custom postprocessing effects.

You can also implement many common postprocessing effects without writing your own compute functions by using image filters from the Metal Performance Shaders framework or Core Image, which also run on the GPU. For information on using the Metal Performance Shaders framework for postprocess effects, see Using Metal performance shaders to create custom postprocess effects. For information on using Core Image for postprocess effects, see Applying core image filters as a postprocess effect.

### Check the output texture pixel format

Some device GPUs require that the output texture be in a specific pixel format. If the device your code is running on doesn’t support MTLGPUFamily.apple2, convert the output texture to MTLPixelFormat.bgra8Unorm before using it. For more information, see Checking the pixel format of a postprocess effect’s output texture.

### Write a compute function

Add a new file to your Xcode project using the Metal File template. It doesn’t matter what filename you choose because Metal loads compute functions by the function name. As long as you include the file that contains the compute function in your build target, Metal is able to find and load it at runtime. A postprocess compute function executes once for each pixel in the rendered scene and is responsible for setting the final color of its pixel.

Here’s a compute function that inverts every pixel of a passed framebuffer.

```
[[kernel]]
void postProcessInvert(uint2 gid [[thread_position_in_grid]],
                       texture2d inColor [[texture(0)]],
                       texture2d outColor [[texture(1)]])
{
    // Check to make sure that the specified thread_position_in_grid value is
    // within the bounds of the framebuffer. This ensures that non-uniform size
    // threadgroups don't trigger an error. For more information, see:
    // https://developer.apple.com/documentation/metal/calculating_threadgroup_and_grid_sizes
    if (gid.x >= inColor.get_width() || gid.y >= inColor.get_height()) {    
        return;
    }

    // Invert the pixel's color by subtracting it from 1.0.
    outColor.write(1.0 - inColor.read(gid), gid);
}
```

Note

For more information on writing postprocess compute functions, see Processing a Texture in a Compute Function.

### Load the compute function

To use the Metal compute function in your postProcess render callback, retrieve the default MTLLibrary, then load your compute function and store the resulting MTLRenderPipelineState object. Load the pipeline state object during startup and store it in a property because you’ll need it in your postprocess callback. A good place to create and store it is in a prepareWithDevice render callback, which RealityKit calls once it has finished its setup but before it renders the next frame and passes it a reference to the MTLDevice where the scene displays. If you assign the callback during app startup, RealityKit calls your method before it renders the first frame.

Here’s an example that loads the invert compute function from above and stores its pipeline state object in a property.

```
func loadPostprocessingShader(device: MTLDevice) {
    guard let library = device.makeDefaultLibrary() else {
        fatalError()
    }

    if let invertKernel = library.makeFunction(name: "postProcessInvert") {
        // Create a pipeline state object and store it in a property.
        invertPipeline = try? device.makeComputePipelineState(function: invertKernel)
    }
} 
```

To make RealityKit call your function, assign it to the prepareWithDevice property of the renderCallbacks property on your ARView during app startup.

```
arView.renderCallbacks.postProcess = loadPostprocessingShader
```

### Create a postprocess callback function

To apply the compute function to the rendered scene, create a callback function that takes a single ARView.PostProcessContext argument and has no return value. In that function, use the command buffer passed in the context to create an MTLComputeCommandEncoder, and assign the pipeline state property you created to that encoder using setComputePipelineState(_:).

Then use setTexture(_:index:) on the encoder to pass the sourceColorTexture and the targetColorTexture to your compute function. If your compute function needs access to additional textures, such as the sourceDepthTexture or a custom texture, you can pass those the same way. Note that the index values used in setTexture(_:index:) must match the value your compute function uses to retrieve the texture.

Because the sample compute function above defines `inColor` as `[[texture(0)]]`, you need to use an index value of `0` when calling setTexture(_:index:) to pass sourceColorTexture. You can also use setBytes(_:length:index:) to pass non-texture data to your compute function. For more information on using that setBytes(_:length:index:) to pass non-texture data, see Passing Structured Data to a Metal Compute Function.

Once you’ve assigned the needed textures and data to the encoder, use dispatchThreads(_:threadsPerThreadgroup:) to start the compute function.

```
func postProcess(context: ARView.PostProcessContext) {
    guard let encoder = context.commandBuffer.makeComputeCommandEncoder() else {
        return
    }

    encoder.setComputePipelineState(pipeline)
    encoder.setTexture(context.sourceColorTexture, index: 0)
    encoder.setTexture(context.compatibleTargetTexture, index: 1)

    let threadsPerGrid = MTLSize(width: context.sourceColorTexture.width,
                                 height: context.sourceColorTexture.height,
                                 depth: 1)

    let w = pixelatePipeline.threadExecutionWidth
    let h = pixelatePipeline.maxTotalThreadsPerThreadgroup / w
    let threadsPerThreadgroup = MTLSizeMake(w, h, 1)

    encoder.dispatchThreads(threadsPerGrid,
                            threadsPerThreadgroup: threadsPerThreadgroup)
    encoder.endEncoding()
}
```

Note

The `compatibleTargetTexture` property referenced above is a derived property based on targetColorTexture. It ensures that the output texture uses the appropriate pixel format for the current device. For more information, see Checking the pixel format of a postprocess effect’s output texture.

### Register the callback function

To apply the effect, register the function as the postProcess render callback for the ARView.

```
arView.renderCallbacks.postProcess = postProcess
```

Note

For more information on writing Metal compute functions to implement postprocess effects, see the Implementing Special Rendering Effects with RealityKit Postprocessing sample code, which demonstrates multiple postprocess techniques, including compute functions.

## See Also

### Metal effects

Using Metal performance shaders to create custom postprocess effects

Leverage the Metal Performance Shaders framework to create special rendering effects for your RealityKit scenes.

Implementing Special Rendering Effects with RealityKit Postprocessing

Implement a variety of postprocessing techniques to alter RealityKit rendering.

Checking the pixel format of a postprocess effect’s output texture

Make sure your postprocess effect works on all devices.

Passing Structured Data to a Metal Compute Function

Send nontexture data from Swift to your Metal shaders using a shared header file.

