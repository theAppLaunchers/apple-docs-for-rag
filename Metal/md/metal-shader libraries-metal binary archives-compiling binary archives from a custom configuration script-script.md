

- Metal
- Shader Libraries
- Metal Binary Archives
-  Compiling Binary Archives from a Custom Configuration Script 

Article

# Compiling Binary Archives from a Custom Configuration Script

Define how the Metal translator builds binary archives without precompiled binaries as a starting source.

## Overview

Creating binary archives for additional GPU architectures, as Creating Binary Archives from Device-Built Pipeline State Objects describes, requires a compiled binary archive. To bypass this restriction, you can hand-author JSON configuration scripts that represent a pipeline state for the Metal translator. Hand-authoring configuration scripts gives you control over defining your pipeline states, and allows you to provide a script section of the JSON for conditional compilation on a per-architecture basis.

This article shows you how to create a Metal translator configuration script that represents a pipeline state, as the following code example demonstrates:

- Swift
- Objective-C

```
static let enableRayTracing = true

do {
    // Creating a variable to mirror the static constant allows for Objective-C bridging.
    var rayTracingBridge = enableRayTracing

    let device = MTLCreateSystemDefaultDevice()
    let library = device.makeLibrary(url: Bundle.main.url(forResource: "render", withExtension: "metallib"))
    let archiveDescriptor = MTLBinaryArchiveDescrptor(url: Bundle.main.url(forResource: "render.binary", withExtension: "metallib"))
    let archive = device.makeBinaryArchive(descriptor: archiveDescriptor)

    let renderPipelineDescriptor = makeRenderDescriptor(library: library, archive: archive)
    let computePipelineDescriptor = makeComputeDescriptor(library: library, archive: archive, rayTracing: &rayTracingBridge)
}
catch {
    FatalError("Error during Metal submission: \(error)")
}
```

```
static const BOOL enableRayTracing = YES;

MTLRenderPipelineDescriptor *makeRenderDescriptor(id, id, NSError**);
MTLComputePipelineDescriptor *makeComputeDescriptor(id, id, NSError**);

NSError *error = nil;

id device = MTLCreateSystemDefaultDevice()
id library = [device newLibraryWithURL:[[NSBundle main] URLForResource:@"render" withExtension:@"metallib"]
    error:&error];

MTLBinaryArchiveDescriptor *archiveDescriptor = [[MTLBinaryArchiveDescriptor alloc] init];
archiveDescriptor.url = [[NSBundle main] URLForResource:@"render.binary" withExtension:@"metallib"];
id archive = [device newBinaryArchiveWithDescriptor:archiveDescriptor error:&error];

MTLRenderPipelineDescriptor *renderPipelineDescrptor = makeRenderDescriptor(library, archive);
MTLComputePipelineDescriptor *computePipelineDescriptor = makeComputeDescriptor(library, archive);
```

The code example above includes a render pipeline with a single-stage fragment and vertex shader, as well as a compute pipeline. The library `render.metallib` contains the Metal IR for the shaders, and `render.binary.metallib` is the binary you generate from the Metal translator. The compute kernel optonally uses ray tracing, depending on the value of `enableRayTracing`, and enabling ray tracing uses intersection functions.

### Create Your Configuration Script and Add Libraries

Create a file named `render.mtlp-json` in the same directory as `render.metallib`, and open it in a text editor. This is the configuration script the Metal translator uses to build your described pipeline states.

Important

The `metal-tt` command-line tool requires that all configuration scripts end with the `mtlp-json` extension.

The basic format of this file is a JSON dictionary containing at least two keys, `libraries` and `pipelines`. The `libraries` key defines which compiled Metal libraries contain your compiled shaders, as an array of paths. Each path is a dictionary with a label that defines how you refer to the library in the configuration script, and a path that points to the library itself. The following code example is the start of a configuration script that sets the alias `LibRender` for the Metal library `render.metallib`:

```
```

### Add Render Pipeline States

Each pipeline in your configuration script needs a reference to shader functions and information about your app’s pipeline state when Metal invokes them. Any optional property that you omit from a pipeline description in the configuration script uses its default value, just as with a pipeline state descriptor instance in code. The code example below creates an MTLRenderPipelineDescriptor instance for both a `vertexFunction` and a `fragmentFunction`. This render pipeline also uses a nondefault MTLPixelFormat.bgra8Unorm pixel format.

- Swift
- Objective-C

```
func makeRenderDescriptor(library: MTLLibrary, archive: MTLBinaryArchive) throws -> MTLRenderPipelineDescriptor {
    let vertexFunctionDescriptor = MTLFunctionDescriptor()
    vertexFunctionDescriptor.name = "vertexShader"
    vertexFunctionDescriptor.binaryArchives = [ archive ]
    let vertexFunction = library.makeFunction(descriptor: vertexFunctionDescriptor)

    let fragmentFunctionDescriptor = MTLFunctionDescriptor()
    fragmentFunctionDescriptor.name = "fragmentShader"
    fragmentFunctionDescriptor.binaryArchives = [ archive ]
    let fragmentFunction = library.makeFunction(descriptor: fragmentFunctionDescriptor)

    let renderPipelineDescriptor = MTLRenderPipelineDescriptor()
    renderPipelineDescriptor.vertexFunction = vertexFunction
    renderPipelineDescriptor.fragmentFunction = fragmentFunction
    renderPipelineDescriptor.colorAttachments[0].pixelFormat = .bgra8Unorm
    renderPipelineDescriptor.binaryArchives = [ archive ]

    return renderPipelineDescriptor
}
```

```
MTLRenderPipelineDescriptor *makeRenderDescriptor(id library, id archive, NSError** error) {
    MTLFunctionDescriptor* vertexDescriptor = [[MTLFunctionDescriptor alloc] init];
    vertexDescriptor.name = @"vertexShader";
    vertexDescriptor.binaryArchives = @[ archive ];
    id vertexFunction = [library newFunctionWithDescriptor:descriptor error:error];

    MTLFunctionDescriptor *fragmentDescriptor = [[MTLFunctionDescriptor alloc] init];
    fragmentDescriptor.name = @"fragmentShader";
    fragmentDescriptor.binaryArchives = @[ archive ];
    id fragmentFunction = [library newFunctionWithDescriptor:descriptor error:error];

    MTLRenderPipelineDescriptor *pipelineStateDescriptor = [[MTLRenderPipelineDescriptor alloc] init];
    pipelineStateDescriptor.vertexFunction = vertexFunction;
    pipelineStateDescriptor.fragmentFunction = fragmentFunction;
    pipelineStateDescriptor.colorAttachments[0].pixelFormat = MTLPixelFormatBGRA8Unorm;

    return pipelineStateDescriptor
}
```

In your translator configuration script, the top-level `pipelines` dictionary contains the definition for each pipeline. Inside this dictionary, the `render_pipelines` key contains an array of dictionaries describing your render pipelines. Function references use a format of `alias:#`.

Dictionaries describing render pipelines need both a `vertex_function` and a `fragment_function` key. The following code example is the JSON configuration script representation of the code above:

```
```

Tip

Full documentation of the configuration script format, including how to conditionally control compilation to binary, is available by running `man metal-pipelines-script` in Terminal.

### Add Compute Pipeline States with Visible and Intersection Functions

In the following code example, the compute kernel uses the ray-tracing intersection function `sphereIntersection` and the visible function `evaluateGeometry`:

- Swift
- Objective-C

```
func makeComputeDescriptor(library: MTLLibrary, archive: archive, rayTracing: UnsafePointer) throws -> MTLComputePipelineDescriptor {
    let sphereFuncDescriptor = MTLFunctionDescriptor()
    sphereFuncDescriptor.name = "sphereIntersection"
    sphereFuncDescriptor.binaryArchives = [ archive ]
    let sphereFunc = library.makeFunction(descriptor: sphereFuncDescriptor)

    let geometryFuncDescriptor = MTLFunctionDescriptor()
    geometryFuncDescriptor.name = "evaluateGeometry"
    geometryFuncDescriptor.binaryArchives = [ archive ]
    let geometryFunc = library.makeFunction(descriptor: geometryFuncDescriptor)

    let linkedFunctions = MTLLinkedFunctions()
    linkedFunctions.functions = [sphereFunc, geometryFunc]
    linkedFunctions.binaryFunctions = [sphereFunc, geometryFunc]

    // The code example continues below.
```

```
MTLComputePipelineDescriptor* makeComputeDescriptor(id library, id archive, NSError** error) {
    fd.name = "sphereIntersection";
    fd.options = MTLFunctionOptionCompileToBinary;
    id sphereIntersectionFunction = [library newFunctionWithDescriptor:fd error:&error];

    fd.name = "evaluateGeometry";
    id evalGeometry = [library newFunctionWithDescriptor:fd error:&error];

    MTLLinkedFunctions *mtlLinkedFunctions = [MTLLinkedFunctions new];
    mtlLinkedFunctions.binaryFunctions = @[sphereIntersectionFunction, evalGeometry];

    // The code example continues below.
```

To add `sphereIntersection` and `evaluateGeometry` to your binary archive, modify the top-level `functions` key of your configuration script. This key’s value is a dictionary that describes the functions available to the Metal translator during compilation. Add the `intersection_functions` key for your intersection functions, and the v`isible_functions` key for visible functions. Each of these keys has an array of dictionaries containing the `function` key, which holds a reference to the function your shaders call.

The following code example is the JSON configuration script representation of the code above for a compute kernel named `rayTracingKernel`. Add the `compute_pipelines` key and value to your existing `pipelines` from adding the render pipeline, along with the new `functions` dictionary.

```
```

Important

Use function names in the `binary_functions` array, not function aliases.

### Add Specialization Constants for Your Compute Pipeline

In this article’s code examples, the `enableRayTracing` constant controls whether the compute kernel uses ray-tracing support. In your app, you use `rayTracingKernel` for the compute kernel’s name, but each constant specializes the function to a single binary representation that has its own name. The following code example sets the specialized function names `rayTracingWithIntersection` and `rayTracingNoIntersection`, depending on the value of `enableRayTracing`:

- Swift
- Objective-C

```
    // Continuing from the code example above.
    let computeSpecialization = MTLFunctionConstantValues()
    computeSpecialization.setConstantValue(&rayTracingBridge, type: .bool, index: 0)

    let rayTracingDescriptor: MTLFunctionDescriptor
    rayTracingDescriptor.name = "rayTracingKernel"
    rayTracingDescriptor.constantValues = computeSpecialization
    rayTracingDescriptor.specializedName = enableRayTracing ? "rayTracingWithIntersection" : "rayTracingNoIntersection"
    rayTracingDescriptor.binaryArchives = [ archive ]

    let rayTracingKernel = library.makeFunction(descriptor: rayTracingDescriptor)

    let computeDescriptor = MTLComputePipelineDescriptor()
    computeDescriptor.computeFunction = rayTracingKernel
    computeDescriptor.linkedFunctions = linkedFunctions
    computeDescriptor.binaryArchives = [ archive ]

    return computeDescriptor
}
```

```
    // Continuing from the code example above.    
    MTLFunctionConstantValues* computeSpecialization = [[MTLFunctionConstantValues alloc] init];
    [computeSpecialization setConstantValue:&enableRayTracing type:MTLDataTypeBool atIndex:0];

    MTLFunctionDescriptor *rayTracingDescriptor = [[MTLFunctionDescriptor alloc] init];
    rayTracingDescriptor.name = @"rayTracingKernel";
    rayTracingDescriptor.constantValues = computeSpecialization;
    rayTracingDescriptor.binaryArchives = @[archive];

    id rayTracingKernel = [library newFunctionWithDescriptor:rayTracingDescriptor error:&error];

    MTLComputePipelineDescriptor *descriptor = [MTLComputePipelineDescriptor new];
    descriptor.computeFunction = rayTracingKernel;
    descriptor.threadGroupSizeIsMultipleOfThreadExecutionWidth = YES;
    descriptor.linkedFunctions = mtlLinkedFunctions;
    computeDescriptor.binaryArchives = @[ archive ];

    return descriptor;
}
```

Your Metal pipeline state contains any constants shaders use, so your JSON configuration script needs to map these constants to a specialized function name. In a Metal translator JSON configuration script, each constant has an `id_type` that defines how the `id` resolves in your app. Constants also have a `value_type` that defines the type of the constant, and a `value` that provides the constant itself. When Metal doesn’t find a specialized function for a constant, the system falls back to compile shaders from Metal IR.

Each constant value is for a `FunctionConstantName` with the identifier `useIntersectionFunctions`, a type of `ConstantBool`. The only difference between the two specialized functions `rayTracingWithIntersection` and `rayTracingNoIntersection` is the `value.data` key, which is `true` for `rayTracingWithIntersection` and `false` for `rayTracingNoIntersection`.

The following code example is the JSON configuration script representation of the code above:

```
```

In addition to including the specialized function definitions for your libraries, provide a separate `pipelines.compute_pipelines` entry for each specialized kernel. Use the label of each specialized function definition, along with the name of your kernel, to refer to the specialization in your configuration script. Write aliases for specialized functions using the format of `alias:#`.

Modify the existing `compile_pipelines` section from the JSON configuration script examples to contain the specializations for your compute pass.

```
```

### Compile Binary Archives

With the Metal IR library and a configuration script that describes a pipeline state matching your app’s code, the Metal translator can compile GPU-specific binaries for any device that supports Metal. In Terminal, run the following `metal-tt` command to build for GPUs targeting iOS 16:

```
% xcrun -sdk iphoneos metal-tt render.metallib render.mtlp-json -o render.binary.metallib -target air64-apple-ios16.0
```

By default, `metal-tt` compiles for all GPU architectures the target triple supports. Run the `metal-lipo` command-line tool in Terminal to confirm the binary archive’s contents.

```
% xcrun metal-lipo render.binary.metallib -archs
applegpu_g10p applegpu_g5p applegpu_g9p applegpu_g9g applegpu_g11p applegpu_g12p applegpu_g13p applegpu_g13g applegpu_g14p applegpu_g14g applegpu_g16p applegpu_g15p
```

### Add the Compiled Binary Archive to Your App

To use your compiled Metal binary archive, you need to add it to your Xcode project’s bundle resources. Add the `precompiled.binary.metallib` archive to your project’s Copy Bundle Resources build phase. For instructions, see Customizing the build phases of a target.

Note

Select the “Copy items if needed” checkbox to ensure the created archive is in your project, and the system doesn’t overwrite or delete it.

In your code, load binary archives by calling makeBinaryArchive(descriptor:) and add the resulting instances to your pipeline state descriptor’s binaryArchives property. For specialized, visible, and intersection functions, load them into an appropriate MTLFunctionDescriptor instance’s binaryArchives property. The code examples throughout this article include sections for linking binary archives when a function has a precompiled shader.

## See Also

### Working with Metal Binary Archives

Creating Binary Archives from Device-Built Pipeline State Objects

Write your Metal pipeline states to a binary archive at app runtime, and build binaries for any supported GPU.

Manipulating Metal Binary Archives

Split precompiled binaries into individual slices, and combine them back together for targeted distribution.

