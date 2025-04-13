

- Metal
- MTLComputePipelineDescriptor
-  maxCallStackDepth 

Instance Property

# maxCallStackDepth

The maximum recursive call depth for dynamic library, visible, and intersection functions.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 16.0+visionOS 1.0+

``` source
var maxCallStackDepth: Int { get set }
```

## Discussion

The maximum call stack depth only applies to indirect function calls in your shader, and indicates the upper bound of stack memory for each thread. Change this value if you use recursive functions in your compute pass, and try to keep it as small as possible. When Metal reserves a large call stack, it can impact performance.

The default value is `1`.

## See Also

### Configuring the Compute Execution Environment

var computeFunction: (any MTLFunction)?

The compute kernel the pipeline calls.

var threadGroupSizeIsMultipleOfThreadExecutionWidth: Bool

A Boolean value that indicates whether the threadgroup size is always a multiple of the thread execution width.

var maxTotalThreadsPerThreadgroup: Int

The maximum number of threads in a threadgroup that you can dispatch to the compute function.

