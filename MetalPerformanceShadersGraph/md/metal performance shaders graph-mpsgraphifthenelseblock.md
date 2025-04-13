

- Metal Performance Shaders Graph
-  MPSGraphIfThenElseBlock 

Type Alias

# MPSGraphIfThenElseBlock

A block of operations executed under either the if or else condition.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
typealias MPSGraphIfThenElseBlock = () -> [MPSGraphTensor]
```

## Return Value

Tensors returned by user. If not empty, the user must define both the then and else blocks, both should have the same number of arguments, and each corresponding argument should have the same element types.

