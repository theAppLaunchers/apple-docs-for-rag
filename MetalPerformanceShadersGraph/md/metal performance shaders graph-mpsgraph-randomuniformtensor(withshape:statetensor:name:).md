

- Metal Performance Shaders Graph
- MPSGraph
-  randomUniformTensor(withShape:stateTensor:name:) 

Instance Method

# randomUniformTensor(withShape:stateTensor:name:)

Creates a RandomUniform operation and returns random uniform values and updated state

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
func randomUniformTensor(
    withShape shape: [NSNumber],
    stateTensor state: MPSGraphTensor,
    name: String?
) -> [MPSGraphTensor]
```

## Parameters 

`shape`  

The shape of the tensor generated

`state`  

The state to define a stream of random values. All calls with equal state yield an identical stream of random values.

`name`  

The name for the operation.

## Return Value

An array of MPSGraphTensor of size 2. The first MPSGraphTensor is of shape containing random values in the defined range. The second MPSGraphTensor is the updated state tensor.

## Discussion

Returns an array of 2 tensors, where the first is a tensor of provided shape of random uniform values in the range \[0.0, 1.0), and the second is the updated state tensor. The provided state is used to define a stream of random values. No state is preserved, and all calls with equal state yield an identical stream of random values. The initial stateTensor provided should be created using the MPSGraph randomPhiloxStateTensor APIs. The resulting stateTensor from this op can be passed as an argument to the following random calls to continue sampling from the stream.

