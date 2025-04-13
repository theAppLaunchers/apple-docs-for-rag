

- Metal Performance Shaders Graph
- MPSGraph
-  randomTensor(withShape:descriptor:stateTensor:name:) 

Instance Method

# randomTensor(withShape:descriptor:stateTensor:name:)

Creates a Random op of type matching distribution in descriptor, and returns random values and updated state.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
func randomTensor(
    withShape shape: [NSNumber],
    descriptor: MPSGraphRandomOpDescriptor,
    stateTensor state: MPSGraphTensor,
    name: String?
) -> [MPSGraphTensor]
```

## Parameters 

`shape`  

The shape of the tensor generated

`descriptor`  

The descriptor of the distribution. See MPSGraphRandomOpDescriptor.

`state`  

The state to define a stream of random values. All calls with equal state yield an identical stream of random values.

`name`  

The name for the operation.

## Return Value

An array of MPSGraphTensor of size 2. The first MPSGraphTensor is of shape containing random values in the defined range. The second MPSGraphTensor is the updated state tensor.

## Discussion

Returns an array of 2 tensors, where the first is of provided shape of random values in the distribution specified, and the second is the updated state tensor. Uses the provided state to define a stream of random values. No state is preserved, and all calls with equal state yield an identical stream of random values. The initial stateTensor provided should be created using the MPSGraph randomPhiloxStateTensor APIs. The resulting stateTensor from this op can be passed as an argument to the following random calls to continue sampling from the stream.

