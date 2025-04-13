

- Metal Performance Shaders Graph
- MPSGraph
-  singleGateRNN(\_:recurrentWeight:initState:descriptor:name:) 

Instance Method

# singleGateRNN(\_:recurrentWeight:initState:descriptor:name:)

Creates a single-gate RNN operation and returns the value and optionally the training state tensor.

iOS 15.4+iPadOS 15.4+Mac Catalyst 15.4+macOS 12.3+tvOS 15.4+visionOS 1.0+

``` source
func singleGateRNN(
    _ source: MPSGraphTensor,
    recurrentWeight: MPSGraphTensor,
    initState: MPSGraphTensor?,
    descriptor: MPSGraphSingleGateRNNDescriptor,
    name: String?
) -> [MPSGraphTensor]
```

## Parameters 

`source`  

A tensor that contains the source data `x[t]` with the data layout \[T,N,I\]. In case `inputWeight = nil` and `bidirectional = NO` then the layout is \[T,N,H\] and for `inputWeight = nil` and `bidirectional = YES` the layout is \[T,N,2H\].

`recurrentWeight`  

A tensor containing the recurrent weights `R`. For `bidirectional` the layout is \[2,H,H\] and otherwise it is \[H,H\].

`initState`  

The initial internal state of the RNN `h[-1]` - optional, if missing the operation assumes zeroes. For `bidirectional` the layout is \[N,2H\] and otherwise it is \[N,H\].

`descriptor`  

A descriptor that defines the parameters for the RNN operation.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor array of size 1 or 2, depending on value of `descriptor.training`. The layout of the both outputs is \[T,N,H\] or \[T,N,2H\] for bidirectional.

## Discussion

This operation returns tensors `h` and optionally `z` that are defined recursively as follows:

```
for t = 0 to T-1
  z[t] = x[t] W^T + (h[t-1]m) R^T + b
  h[t] = activation( z[t] ), where
```

`W` is optional `inputWeight`, `R` is `recurrentWeight`, `b` is `bias`, `m` is optional `mask`, `x[t]` is `source` `h[t]` is the first output, `z[t]` is the second output (optional) and `h[-1]` is `initState`. See MPSGraphSingleGateRNNDescriptor for different `activation` options.

