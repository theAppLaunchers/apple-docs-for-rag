Framework

# Metal

Render advanced 3D graphics and compute data in parallel with graphics processors.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.11+tvOS 9.0+visionOS 1.0+

## [Overview](/documentation/Metal#overview)

The Metal framework gives your app direct access to a device’s graphics processing unit (GPU). With Metal, apps can leverage a GPU to quickly render complex scenes and run computational tasks in parallel. For example, apps in these categories use Metal to maximize their performance:

*   Games that render sophisticated 2D or 3D environments
    
*   Video processing apps, like Final Cut Pro
    
*   Scientific research apps that analyze and process large datasets
    
*   Fully immersive visionOS apps
    

Metal works hand-in-hand with other frameworks that supplement its capability. For example, [MetalFX](/documentation/MetalFX) upscales your renderings in less time than rendering them natively, and [MetalKit](/documentation/MetalKit) simplifies the tasks that display your Metal content onscreen. The [Metal Performance Shaders](/documentation/metalperformanceshaders) framework provides a large library of optimized compute and rendering shaders that take advantage of each GPU’s unique hardware. In visionOS, create fully immersive stereoscopic content with the help of the [Compositor Services](/documentation/CompositorServices) framework.

Many high-level Apple frameworks leverage the performance of Metal, including [RealityKit](/documentation/RealityKit), [SceneKit](/documentation/SceneKit), [SpriteKit](/documentation/SpriteKit), and [Core Image](/documentation/CoreImage). These high-level frameworks implement the GPU programming details for you. However, you can typically get better performance by writing your own custom Metal and shader code. See the [Metal Shading Language Specification](https://developer.apple.com/metal/Metal-Shading-Language-Specification.pdf) for shader implementation details.

## [Topics](/documentation/Metal#topics)

### [Essentials](/documentation/Metal#Essentials)

Begin with the Metal fundamentals.

[

Understanding the Metal 4 core API](/documentation/metal/understanding-the-metal-4-core-api)

Discover the features and functionality in the Metal 4 foundational APIs.

[

Using a Render Pipeline to Render Primitives](/documentation/metal/using-a-render-pipeline-to-render-primitives)

Render a colorful, 2D triangle by running a draw command on the GPU.

[

Performing Calculations on a GPU](/documentation/metal/performing-calculations-on-a-gpu)

Use Metal to find GPUs and perform calculations on them.

[

Using Metal to Draw a View’s Contents](/documentation/metal/using-metal-to-draw-a-view's-contents)

Create a MetalKit view and a render pass to draw the view’s contents.

### [Samples](/documentation/Metal#Samples)

Discover graphics techniques and Metal features through sample code projects.

[

API Reference

Metal Sample Code Library](/documentation/metal/metal-sample-code-library)

Explore the complete set of Metal samples.

### [GPU Devices](/documentation/Metal#GPU-Devices)

Start with a Metal device instance to begin working with the GPU it represents.

[

API Reference

GPU Devices and Work Submission](/documentation/metal/gpu-devices-and-work-submission)

Find any available GPU, submit work to it with command buffers, suspend work, and coordinate between multiple GPUs.

### [Command Encoders](/documentation/Metal#Command-Encoders)

Send work to a GPU by issuing commands and configuring the pipeline states for those commands.

[

API Reference

Render Passes](/documentation/metal/render-passes)

Encode a render pass to draw graphics into an image.

[

API Reference

Compute Passes](/documentation/metal/compute-passes)

Encode a compute pass that runs computations in parallel on a thread grid, processing and manipulating Metal resource data on multiple cores of a GPU.

[

API Reference

Machine-Learning Passes](/documentation/metal/machine-learning-passes)

Add machine-learning model inference to your Metal app’s GPU workflow.

[

API Reference

Blit Passes](/documentation/metal/blit-passes)

Encode a block information transfer pass to adjust and copy data to and from GPU resources, such as buffers and textures.

[

API Reference

Indirect Command Encoding](/documentation/metal/indirect-command-encoding)

Store draw commands in Metal buffers and run them at a later time on the GPU, either once or repeatedly.

[

API Reference

Ray Tracing with Acceleration Structures](/documentation/metal/ray-tracing-with-acceleration-structures)

Build a representation of your scene’s geometry using triangles and bounding volumes to quickly trace rays through the scene.

### [Resources](/documentation/Metal#Resources)

Store data in buffers and textures, and optionally manage the underlying GPU memory yourself.

[

API Reference

Resource Fundamentals](/documentation/metal/resource-fundamentals)

Control the common attributes of all Metal memory resources, including buffers and textures, and how to configure their underlying memory.

[

API Reference

Buffers](/documentation/metal/buffers)

Create and manage untyped data your app uses to exchange information with its shader functions.

[

API Reference

Textures](/documentation/metal/textures)

Create and manage typed data your app uses to exchange information with its shader functions.

[

API Reference

Memory Heaps](/documentation/metal/memory-heaps)

Take control of your app’s GPU memory management by creating a large memory allocation for various buffers, textures, and other resources.

[

API Reference

Resource Loading](/documentation/metal/resource-loading)

Load assets in your games and apps quickly by running a dedicated input/output queue alongside your GPU tasks.

[

API Reference

Resource Synchronization](/documentation/metal/resource-synchronization)

Prevent multiple commands that can access the same resources simultaneously by coordinating those accesses with barriers, fences, or events.

### [Shader Compilation and Libraries](/documentation/Metal#Shader-Compilation-and-Libraries)

Compile and organize shaders, the GPU functions that run on a Metal device’s execution units.

[

Using the Metal 4 compilation API](/documentation/metal/using-the-metal-4-compilation-api)

Control when and how you compile an app’s shaders.

[

API Reference

Shader Libraries](/documentation/metal/shader-libraries)

Manage and load your app’s Metal shaders.

[

Using Function Specialization to Build Pipeline Variants](/documentation/metal/using-function-specialization-to-build-pipeline-variants)

Create pipelines for different levels of detail from a common shader source.

### [Presentation](/documentation/Metal#Presentation)

Display standard or high-dynamic-range content on a device’s display with [Core Animation](/documentation/QuartzCore) or [MetalKit](/documentation/MetalKit), in standard or high dynamic range.

[

Managing your game window for Metal in macOS](/documentation/metal/managing-your-game-window-for-metal-in-macos)

Set up a window and view for optimally displaying your Metal content.

[

Adapting your game interface for smaller screens](/documentation/metal/adapting-your-game-interface-for-smaller-screens)

Make text legible on all devices the player chooses to run your game on.

[

API Reference

Onscreen Presentation](/documentation/metal/onscreen-presentation)

Show the output from a GPU’s rendering pass to the user in your app.

[

API Reference

HDR Content](/documentation/metal/hdr-content)

Take advantage of high dynamic range to present more vibrant colors in your apps and games.

### [Developer Tools](/documentation/Metal#Developer-Tools)

Identify and fix issues with your app’s Metal API calls, shader code, resources, and performance during development by using Metal Debugger.

[

Supporting Simulator in a Metal app](/documentation/metal/supporting-simulator-in-a-metal-app)

Configure alternative render paths in your Metal app to enable running your app in Simulator.

[

Capturing Metal Commands Programmatically](/documentation/metal/capturing-metal-commands-programmatically)

Invoke Metal’s frame capture from your app, then save the resulting GPU trace to a file or view it in Xcode.

[

Logging shader debug messages](/documentation/metal/logging-shader-debug-messages)

Print debugging messages that a shader generates using shader logging.

[

Developing Metal apps that run in Simulator](/documentation/metal/developing-metal-apps-that-run-in-simulator)

Prototype and test your Metal apps in Simulator.

[

Improving your game’s graphics performance and settings](/documentation/metal/improving-your-games-graphics-performance-and-settings)

Fix performance glitches and develop default settings for smooth experiences on Apple platforms using the powerful suite of Metal development tools.

[

Metal debugger](/documentation/Xcode/Metal-debugger)

Debug and profile your Metal workload with a GPU trace.

[

Metal developer workflows](/documentation/Xcode/Metal-developer-workflows)

Locate and fix issues related to your app’s use of the Metal API and GPU functions.

[

API Reference

GPU Counters and Counter Sample Buffers](/documentation/metal/gpu-counters-and-counter-sample-buffers)

Retrieve runtime data from a GPU device by sampling one or more of its counters.

[

API Reference

Metal Debugging Types](/documentation/metal/metal-debugging-types)

Create capture managers and capture scopes, and review a GPU device’s log after it runs a command buffer.

### [Apple Silicon](/documentation/Metal#Apple-Silicon)

Take advantage of the unique architecture of Apple silicon GPUs.

[

Porting your Metal code to Apple silicon](/documentation/Apple-Silicon/porting-your-metal-code-to-apple-silicon)

Create a version of your Metal app that runs on both Apple silicon and Intel-based Mac computers.

[

Tailor Your Apps for Apple GPUs and Tile-Based Deferred Rendering](/documentation/metal/tailor-your-apps-for-apple-gpus-and-tile-based-deferred-rendering)

Learn about characteristic Apple GPU features, including imageblocks, tile shaders, and raster order groups.

### [Reference](/documentation/Metal#Reference)

[

API Reference

Metal Structures](/documentation/metal/metal-structures)

[

API Reference

Metal Enumerations](/documentation/metal/metal-enumerations)

[

API Reference

Metal Constants](/documentation/metal/metal-constants)

[

API Reference

Metal Data Types](/documentation/metal/metal-data-types)

[

API Reference

Metal Variables](/documentation/metal/metal-variables)

## [See Also](/documentation/Metal#see-also)

### [Related Documentation](/documentation/Metal#Related-Documentation)

[Metal Programming Guide](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014221)

[Metal Best Practices Guide](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/index.html#//apple_ref/doc/uid/TP40016642)