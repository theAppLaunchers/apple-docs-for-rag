

- Metal Performance Shaders Graph
- MPSGraph
-  LSTM(\_:recurrentWeight:inputWeight:bias:initState:initCell:mask:peephole:descriptor:name:) 

Instance Method

# LSTM(\_:recurrentWeight:inputWeight:bias:initState:initCell:mask:peephole:descriptor:name:)

Creates an LSTM operation and returns the value tensor and optionally the cell state tensor and the training state tensor.

iOS 15.4+iPadOS 15.4+Mac Catalyst 15.4+macOS 12.3+tvOS 15.4+visionOS 1.0+

``` source
func LSTM(
    _ source: MPSGraphTensor,
    recurrentWeight: MPSGraphTensor,
    inputWeight: MPSGraphTensor?,
    bias: MPSGraphTensor?,
    initState: MPSGraphTensor?,
    initCell: MPSGraphTensor?,
    mask: MPSGraphTensor?,
    peephole: MPSGraphTensor?,
    descriptor: MPSGraphLSTMDescriptor,
    name: String?
) -> [MPSGraphTensor]
```

## Parameters 

`source`  

A tensor containing the source data `x[t]` with the data layout \[T,N,I\]. In case `inputWeight = nil` and `bidirectional = NO` then the layout is \[T,N,4H\] and for `inputWeight = nil` and `bidirectional = YES` the layout is \[T,N,8H\].

`recurrentWeight`  

A tensor containing the recurrent weights `R`. For `bidirectional` the layout is \[2,4H,H\] and otherwise it is \[4H,H\].

`inputWeight`  

A tensor containing the input weights matrix `W` - optional, if missing the operation assumes a diagonal unit-matrix. For `bidirectional` the layout is \[8H,I\] and otherwise it is \[4H,I\].

`bias`  

A tensor containing the bias `b` - optional, if missing the operation assumes zeroes. For `bidirectional` the layout is \[8H\] and otherwise it is \[4H\].

`initState`  

The initial internal state of the LSTM `h[-1]` - optional, if missing the operation assumes zeroes. For `bidirectional` the layout is \[N,2H\] and otherwise it is \[N,H\].

`initCell`  

The initial internal cell of the LSTM `h[-1]` - optional, if missing the operation assumes zeroes. For `bidirectional` the layout is \[N,2H\] and otherwise it is \[N,H\].

`mask`  

A tensor containing the mask `m` - optional, if missing the operation assumes ones. Useful for dropout.

`peephole`  

A tensor containing the peephole vector `v` - optional, if missing the operation assumes zeroes. Shape is \[4H\], ie. a vector for each gate, or \[2,4H\] for bidirectional.

`descriptor`  

A descriptor that defines the parameters for the LSTM operation.

`name`  

The name for the operation.

## Return Value

A valid `MPSGraphTensor` array of size 1 or 2 or 3, depending on values of `descriptor.produceCell` and `descriptor.training`. The layout of the both state and cell outputs are \[T,N,H\] or \[T,N,2H\] for bidirectional, and the layout of the trainingState output is \[T,N,4H\] or \[T,N,8H\] for bidirectional.

## Discussion

This operation returns tensors `h` and optionally `c` and optionally `z` that are defined recursively as follows:

```
for t = 0 to T-1
  z[t] = [i, f, z, o][t] = f( (h[t-1] m) R^T + x'[t] + p c[t-1] )
  x'[t] = x[t] W^T + b
  c[t] = f[t]c[t-1] + i[t]z[t]
  h[t] = o[t]g(c[t]), where
```

`W` is optional `inputWeight`, `R` is `recurrentWeight`, `b` is optional `bias`, `m` is optional `mask`, `x[t]` is `source` `h[t]` is the first output, `c[t]` is the second output (optional), `z[t]` is either the second or third output (optional), `h[-1]` is `initCell`. and `h[-1]` is `initState`. `p` is an optional peephole vector. See MPSGraphLSTMDescriptor for different `activation` options for `f()` and `g()`.

