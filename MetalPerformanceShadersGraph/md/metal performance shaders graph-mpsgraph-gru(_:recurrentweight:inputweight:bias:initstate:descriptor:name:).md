

- Metal Performance Shaders Graph
- MPSGraph
-  GRU(\_:recurrentWeight:inputWeight:bias:initState:descriptor:name:) 

Instance Method

# GRU(\_:recurrentWeight:inputWeight:bias:initState:descriptor:name:)

Creates a GRU operation and returns the value and optionally the training state tensor.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

``` source
func GRU(
    _ source: MPSGraphTensor,
    recurrentWeight: MPSGraphTensor,
    inputWeight: MPSGraphTensor?,
    bias: MPSGraphTensor?,
    initState: MPSGraphTensor?,
    descriptor: MPSGraphGRUDescriptor,
    name: String?
) -> [MPSGraphTensor]
```

## Parameters 

`source`  

A tensor containing the source data `x[t]` with the data layout \[T,N,I\]. In case `inputWeight = nil` and `bidirectional = NO` then the layout is \[T,N,3H\] and for `inputWeight = nil` and `bidirectional = YES` the layout is \[T,N,6H\].

`recurrentWeight`  

A tensor containing the recurrent weights `R`. For `bidirectional` the layout is \[2,3H,H\] and otherwise it is \[3H,H\].

`inputWeight`  

A tensor containing the input weights matrix `W` - optional, if missing the operation assumes a diagonal unit-matrix. For `bidirectional` the layout is \[6H,I\] and otherwise it is \[3H,I\].

`bias`  

A tensor containing the bias `b` - optional, if missing the operation assumes zeroes. For `bidirectional` the layout is \[6H\] and otherwise it is \[3H\].

`initState`  

The initial internal state of the LSTM `h[-1]` - optional, if missing the operation assumes zeroes. For `bidirectional` the layout is \[N,2H\] and otherwise it is \[N,H\].

`descriptor`  

A descriptor that defines the parameters for the GRU operation.

`name`  

The name for the operation.

## Return Value

A valid `MPSGraphTensor` array of size 1 or 2 depending on value of `descriptor.training`. The layout of the state output is \[T,N,H\] or \[T,N,2H\] for bidirectional, and the layout of the `trainingState` output is \[T,N,3H\] or \[T,N,6H\] for bidirectional.

## Discussion

This operation returns tensors `h` and optionally `z` that are defined recursively as follows:

```
for t = 0 to T-1
  z[t] = fz( (h[t-1] m) R^T + x[t] W^T + b ),
  r[t] = fr( (h[t-1] m) R^T + x[t] W^T + b ),
  c[t] = (h[t-1] r[t] m) R^T
  o[t] = fo( c[t] + x[t] W^T + b )
  h[t] = z[t]h[t-1] + (1-z[t])o[t]
```

If `resetAfter = YES` then `c[t]` is replaced by

```
  c[t] = ( (h[t-1] m) R^T + b2 ) r[t]
```

If `flipZ = YES` then `h[t]` is replaced by

```
  h[t] = (1-z[t])h[t-1] + z[t]o[t].
```

`W` is optional `inputWeight`, `R` is `recurrentWeight`, `b` is optional `bias`, `m` is optional `mask`, `x[t]` is `source` `h[t]` is the first output, `z[t]` is the second output (optional) and `h[-1]` is `initState`. `b2` is an optional `resetBias` vector, only used when `resetAfter = YES`. See MPSGraphGRUDescriptor for different `activation` options for `f()`.

