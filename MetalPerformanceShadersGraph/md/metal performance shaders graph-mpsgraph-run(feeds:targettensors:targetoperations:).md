

- Metal Performance Shaders Graph
- MPSGraph
-  run(feeds:targetTensors:targetOperations:) 

Instance Method

# run(feeds:targetTensors:targetOperations:)

Runs the graph for the given feeds and returns the target tensor values, ensuring all target operations also executed.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
func run(
    feeds: [MPSGraphTensor : MPSGraphTensorData],
    targetTensors: [MPSGraphTensor],
    targetOperations: [MPSGraphOperation]?
) -> [MPSGraphTensor : MPSGraphTensorData]
```

## Parameters 

`feeds`  

Feeds dictionary for the placeholder tensors.

`targetTensors`  

Tensors for which the caller wishes MPSGraphTensorData to be returned.

`targetOperations`  

Operations to be completed at the end of the run.

## Return Value

A valid MPSGraphTensor : MPSGraphTensorData dictionary with results synchronized to the CPU memory.

## Discussion

This call blocks until execution has completed.

