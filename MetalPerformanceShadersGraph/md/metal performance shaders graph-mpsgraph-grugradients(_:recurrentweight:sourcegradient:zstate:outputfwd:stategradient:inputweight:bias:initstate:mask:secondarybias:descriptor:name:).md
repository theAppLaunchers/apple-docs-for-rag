

- Metal Performance Shaders Graph
- MPSGraph
-  GRUGradients(\_:recurrentWeight:sourceGradient:zState:outputFwd:stateGradient:inputWeight:bias:initState:mask:secondaryBias:descriptor:name:) 

Instance Method

# GRUGradients(\_:recurrentWeight:sourceGradient:zState:outputFwd:stateGradient:inputWeight:bias:initState:mask:secondaryBias:descriptor:name:)

Creates a GRU gradient operation and returns the gradient tensor values.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

``` source
func GRUGradients(
    _ source: MPSGraphTensor,
    recurrentWeight: MPSGraphTensor,
    sourceGradient: MPSGraphTensor,
    zState: MPSGraphTensor,
    outputFwd: MPSGraphTensor,
    stateGradient: MPSGraphTensor?,
    inputWeight: MPSGraphTensor?,
    bias: MPSGraphTensor?,
    initState: MPSGraphTensor?,
    mask: MPSGraphTensor?,
    secondaryBias: MPSGraphTensor?,
    descriptor: MPSGraphGRUDescriptor,
    name: String?
) -> [MPSGraphTensor]
```

## Parameters 

`source`  

A tensor containing the source data `x[t]` with the data layout \[T,N,I\]. In case `inputWeight = nil` and `bidirectional = NO` then the layout is \[T,N,3H\] and for `inputWeight = nil` and `bidirectional = YES` the layout is \[T,N,6H\].

`recurrentWeight`  

A tensor containing the recurrent weights `R`. For `bidirectional` the layout is \[2,3H,H\] and otherwise it is \[3H,H\].

`sourceGradient`  

The input gradient, that is the gradient of a tensor with respect to the first output of the forward pass.

`zState`  

The second output of GRU(_:recurrentWeight:inputWeight:bias:initState:descriptor:name:) with `descriptor.training = YES`.

`outputFwd`  

The first output of GRU(_:recurrentWeight:inputWeight:bias:initState:descriptor:name:) with `descriptor.training = YES`.

`stateGradient`  

The input gradient for state coming from the future timestep - optional, if missing the operation assumes zeroes.

`inputWeight`  

A tensor containing the input weights matrix `W` - optional, if missing the operation assumes a diagonal unit-matrix. For `bidirectional` the layout is \[6H,I\] and otherwise it is \[3H,I\].

`bias`  

A tensor containing the bias `b` - optional, if missing the operation assumes zeroes. For `bidirectional` the layout is \[6H\] and otherwise it is \[3H\].

`initState`  

The initial internal state of the LSTM `h[-1]` - optional, if missing the operation assumes zeroes. For `bidirectional` the layout is \[N,2H\] and otherwise it is \[N,H\].

`mask`  

A tensor containing the mask `m` - optional, if missing the operation assumes ones. Useful for dropout.

`secondaryBias`  

A tensor containing the secondary bias vector `b2` - optional, if missing the operation assumes zeroes. Only used with `reset_after = YES`. Shape is \[H\], ie. a vector for each gate, or \[2H\] for bidirectional.

`descriptor`  

A descriptor that defines the parameters for the GRU operation.

`name`  

The name for the operation.

## Return Value

A valid `MPSGraphTensor` array containing gradients for each input tensor, except for `sourceGradient` and `mask`. In case an input is nil, no gradient will be returned for it. The order of the gradients will be: for `source`, for `recurrentWeight`, for `inputWeight`, for `bias`, for `initState` and for `secondaryBias`.

## Discussion

For details of this operation and parameters, refer to documentation of GRU(_:recurrentWeight:inputWeight:bias:initState:mask:secondaryBias:descriptor:name:).

