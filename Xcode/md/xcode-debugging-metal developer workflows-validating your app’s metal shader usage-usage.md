

- Xcode
- Debugging
- Metal developer workflows
-  Validating your app’s Metal shader usage 

Article

# Validating your app’s Metal shader usage

Catch common shader runtime issues using Shader Validation while your app is running.

## Overview

The Shader Validation layer detects errors only discoverable during shader execution, like out-of-bounds memory accesses, attempts to access `nil` textures, and others. It’s similar to Address Sanitizer for general runtime issues (see Diagnosing memory, thread, and crash issues early). You can enable Shader Validation using the runtime diagnostics options in Xcode, or by using environment variables.

To ensure you see the most up-to-date debug information, set your app’s deployment target to the matching OS version, even if temporarily. You can change the deployment target in the Xcode project settings. If you change the deployment target temporarily, remember to change it back before deploying your app.

Important

The Shader Validation layer has a corresponding impact on GPU performance, and shaders might take longer to compile in runtime. This layer adds instrumentation code to all your GPU functions, which increases the number of times they access memory.

For more information, see the WWDC20 video Debug GPU-side errors in Metal and the WWDC21 video Discover Metal debugging, profiling, and asset creation tools.

### Enable Shader Validation in Xcode

Follow these steps to enable Shader Validation using the runtime diagnostics options in the Scheme settings:

1.  In the Xcode toolbar, choose Edit Scheme from the Scheme menu. Alternatively, choose Product \> Scheme \> Edit Scheme.

2.  In the Edit Scheme panel, select Run.

3.  In the setting tab, click Diagnostics.

4.  Select Shader Validation to enable it, and click Close.

Now the system enables Shader Validation each time you run your scheme.

In addition, you can create breakpoints for shader errors by clicking the arrow next to the Shader Validation checkbox.

### Selectively enable Shader Validation

When enabling Shader Validation, you can also choose to only enable (or disable) Shader Validation for specific pipelines. This advanced control can be particularly useful when you want to focus your debugging on a range of pipelines you preliminarily identified. It can also greatly improve the performance of the apps you debug, thanks to the reduced amount of instrumented pipelines.

Shader Validation instruments all pipelines by default (`MTL_SHADER_VALIDATION_DEFAULT_STATE=all`). To change this behavior, you can set `MTL_SHADER_VALIDATION_DEFAULT_STATE=none`.

Next, you can set `MTL_SHADER_VALIDATION_ENABLE_PIPELINES` and `MTL_SHADER_VALIDATION_DISABLE_PIPELINES` to selectively enable and disable instrumentation for given pipelines. You can use the pipeline labels and Shader Validation unique identifiers (UIDs) as entries (see Print pipeline UIDs). Multiple entries need to be comma-separated, without spaces (see `man MetalValidation` for more information). In the following example, the pipelines with the label `foo` are the only pipelines not instrumented by Shader Validation.

- Swift
- Objective-C

```
let descriptor = MTLRenderPipelineDescriptor()
descriptor.label = "foo"

let pipelineState = try? device.makeRenderPipelineState(descriptor: descriptor)
```

```
MTLRenderPipelineDescriptor* descriptor = [[MTLRenderPipelineDescriptor alloc] init];
descriptor.label = @"foo";

id pipelineState = [device newRenderPipelineStateWithDescriptor:descriptor error:nil];
```

```
> export MTL_SHADER_VALIDATION=1
> export MTL_SHADER_VALIDATION_DEFAULT_STATE=all
> export MTL_SHADER_VALIDATION_DISABLE_PIPELINES="foo"
...

> ./
```

Alternatively, you can programmatically set your pipeline descriptor property shaderValidation to either MTLShaderValidation.enabled or MTLShaderValidation.disabled.

In the following example, `pipelineState` is the only pipeline instrumented by Shader Validation.

- Swift
- Objective-C

```
let descriptor = MTLRenderPipelineDescriptor()
descriptor.shaderValidation = MTLShaderValidation.enabled

let pipelineState = try? device.makeRenderPipelineState(descriptor: descriptor)
```

```
MTLRenderPipelineDescriptor* descriptor = [[MTLRenderPipelineDescriptor alloc] init];
descriptor.shaderValidation = MTLShaderValidationEnabled;

id pipelineState = [device newRenderPipelineStateWithDescriptor:descriptor error:nil];
```

```
> export MTL_SHADER_VALIDATION=1
> export MTL_SHADER_VALIDATION_DEFAULT_STATE=none
> ...

> ./
```

Finally, you can query the Shader Validation state of a pipeline through the shaderValidation property of pipeline state objects.

### Print pipeline UIDs

Shader Validation generates UIDs for all pipelines you process, which you can use as an entry to `MTL_SHADER_VALIDATION_ENABLE_PIPELINES` and `MTL_SHADER_VALIDATION_DISABLE_PIPELINES`. This is useful in the absence of pipeline labels in the application you want to debug.

To print the UIDs to Console or a `log stream` instance, set `MTL_SHADER_VALIDATION_DUMP_PIPELINES=1` in your terminal or Xcode Environment Variables Scheme settings.

Note

To see the logs, go to Action \> Include Debug Messages in Console.

### View Shader Validation errors

After enabling Shader Validation, if Metal encounters errors while executing the commands in a command buffer, the details shown here appear in Xcode:

You can find the breakpoint in the Breakpoint navigator if you want to modify or remove it in the future. For more information, see Setting breakpoints to pause your running app.

If you discover an error in your shader, consider taking a capture and investigating with the shader debugger (see Investigating visual artifacts).

### Enable Shader Validation with environment variables

You can also enable Shader Validation by setting the following environment variables on your Metal app:

MTL_SHADER_VALIDATION=1  
Enables all Shader Validation tests.

MTL_SHADER_VALIDATION_ENABLE_ERROR_REPORTING=1  
Enables Shader Validation error reporting.

MTL_SHADER_VALIDATION_COMPILER_INLINING  
Determines the amount of code inlining that occurs. Possible values are `default` and `full`. Setting the value to `full` forces inlining. Increasing inlining can result in improved runtime performance at the cost of compile time performance. Decreasing inlining can result in improved compile time performance at the cost of runtime performance.

MTL_SHADER_VALIDATION_FAIL_MODE  
Sets the behavior for handling invalid accesses. Possible values are `zerofill` (default) and `allow`. `zerofill` causes invalid reads to return `0`, and drops any invalid writes. `allow` allows an invalid read or write, but can result in command buffer failure, depending on the platform. It also reduces compile and runtime performance impact.

MTL_SHADER_VALIDATION_GLOBAL_MEMORY=1  
Checks all global memory accesses. Accessing invalid memory follows the behavior that `MTL_SHADER_VALIDATION_FAIL_MODE` specifies.

MTL_SHADER_VALIDATION_THREADGROUP_MEMORY=1  
Checks all threadgroup memory accesses. Accessing invalid memory follows the behavior that `MTL_SHADER_VALIDATION_FAIL_MODE` specifies.

MTL_SHADER_VALIDATION_TEXTURE_USAGE=1  
Checks all texture member functions, such as `read`, `write`, `get_width`, and so on. Metal honors your setting for `MTL_SHADER_VALIDATION_FAIL_MODE` when an app triggers an invalid texture operation, including accessing a `nil` texture instance, a valid but nonresident texture instance, a resident texture instance that’s a type that doesn’t match the shader’s signature, or a resident texture instance that doesn’t have an appropriate MTLResourceUsage configuration from one of the resource usage methods of an MTLComputeCommandEncoder or MTLRenderCommandEncoder instance (see Argument Buffer Resource Preparation Commands).

MTL_SHADER_VALIDATION_STACK_OVERFLOW=1  
Checks all indirect calls (calls by function pointer, visible functions, intersection functions, and dynamic libraries), as well as recursive calls. If the call stack depth for such functions exceeds the value in `maxCallStackDepth` for that stage, an error occurs and the system skips the function call.

For a complete list of settings, run `man MetalValidation` in Terminal.

If you discover an error in your shader, consider taking a capture (see Capturing a Metal workload programmatically) and investigating with the Metal debugger (see Debugging the shaders within a draw command or compute dispatch).

## See Also

### Runtime diagnostics

Inspecting live resources at runtime

Validate your resources by viewing the contents of your textures and buffers while debugging your Metal app.

Validating your app’s Metal API usage

Catch runtime issues in your Metal app using API Validation.

Monitoring your Metal app’s graphics performance

Catch performance issues using the Metal Performance HUD while your app is running.

