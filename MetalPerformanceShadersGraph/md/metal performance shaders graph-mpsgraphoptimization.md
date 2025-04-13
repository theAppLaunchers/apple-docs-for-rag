

- Metal Performance Shaders Graph
-  MPSGraphOptimization 

Enumeration

# MPSGraphOptimization

The optimization levels to trade compilation time for even more runtime performance by running more passes.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
enum MPSGraphOptimization
```

## Topics

### Enumeration Cases

case level0

Graph performs core optimizations only.

case level1

Graph performs additional Optimizations, like using the placement pass to dispatch across different HW blocks like the NeuralEngine and CPU along with the GPU.

### Initializers

init?(rawValue: UInt64)

## Relationships

### Conforms To

- BitwiseCopyable
- Equatable
- Hashable
- RawRepresentable
- Sendable

