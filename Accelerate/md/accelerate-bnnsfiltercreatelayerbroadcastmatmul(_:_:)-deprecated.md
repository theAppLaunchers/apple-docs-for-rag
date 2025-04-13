

- Accelerate
-  BNNSFilterCreateLayerBroadcastMatMul(\_:\_:) Deprecated

Function

# BNNSFilterCreateLayerBroadcastMatMul(\_:\_:)

Returns a new broadcast matrix multiply layer.

iOS 14.0–18.0DeprecatediPadOS 14.0–18.0DeprecatedMac Catalyst 14.0–18.0DeprecatedmacOS 11.0–15.0DeprecatedtvOS 14.0–18.0DeprecatedvisionOS 1.0–2.0DeprecatedwatchOS 7.0–11.0Deprecated

``` source
func BNNSFilterCreateLayerBroadcastMatMul(
    _ layer_params: UnsafePointer,
    _ filter_params: UnsafePointer?
) -> BNNSFilter?
```

Deprecated

Use BNNSGraph\* APIs

## Parameters 

`layer_params`  

Layer parameters.

`filter_params`  

The filter runtime parameters.

## Discussion

Use broadcast matrix to perform matrix multiplication on the last two indices of two tensors.

In a case where one tensor has a higher rank (that is, the number of dimensions) than the other, the lower rank matrix is broadcast in the missing dimensions. The operation broadcasts dimensions with a size of one to match the size of the corresponding dimension in the other tensor. For example, given the following data that describes two 3D matrices of two columns, four rows, and three channels:

```
let inputValues: [Float] = [
    // Batch 0, channel 0.
    11, 21,
    31, 41,
    51, 61,
    71, 81,

    // Batch 0, channel 1.
    101, 201,
    301, 401,
    501, 601,
    701, 801,

    // Batch 0, channel 2.
    1001, 2001,
    3001, 4001,
    5001, 6001,
    7001, 8001,

    // Batch 1, channel 0.
    12, 22,
    32, 42,
    52, 62,
    72, 82,

    // Batch 1, channel 1.
    102, 202,
    302, 402,
    502, 602,
    702, 802,

    // Batch 1, channel 2.
    1002, 2002,
    3002, 4002,
    5002, 6002,
    7002, 8002
]
```

Broadcast matrix multiplication provides the functionality to multiply the 3D data in `inputValues` by a 2D matrix by braodcasting it across the missing dimension. In this example, the second matrix contains the following values:

```
var weightsValues: [Float] = [
    2, 0,
    0, 2
]
```

The following code creates `BNNSNDArrayDescriptor` structures to describe the two inputs and the output. Note that the code passes the second input, `weights`, to the parameters structure with b_is_weights set to `true`. This means that the filter stores the data pointer to `weights`, and you don’t need to pass the weights data to the apply call.

```
let batchSize = 2

let i_desc = BNNSNDArrayDescriptor(flags: BNNSNDArrayFlags(0),
                                   layout: BNNSDataLayoutImageCHW,
                                   size: (3, 4, 2, 0, 0, 0, 0, 0),
                                   stride: (0, 0, 0, 0, 0, 0, 0, 0),
                                   data: nil,
                                   data_type: .float,
                                   table_data: nil,
                                   table_data_type: .float,
                                   data_scale: 1,
                                   data_bias: 0)

weightsValues.withUnsafeMutableBufferPointer { weightsPtr in
    let w_desc = BNNSNDArrayDescriptor(flags: BNNSNDArrayFlags(0),
                                       layout: BNNSDataLayoutRowMajorMatrix,
                                       size: (2, 2, 0, 0, 0, 0, 0, 0),
                                       stride: (0, 0, 0, 0, 0, 0, 0, 0),
                                       data: weightsPtr.baseAddress,
                                       data_type: .float,
                                       table_data: nil,
                                       table_data_type: .float,
                                       data_scale: 1,
                                       data_bias: 0)

    let o_desc = BNNSNDArrayDescriptor(flags: BNNSNDArrayFlags(0),
                                       layout: BNNSDataLayoutImageCHW,
                                       size: (i_desc.size.0, i_desc.size.1, w_desc.size.1, 0, 0, 0, 0, 0),
                                       stride: (0, 0, 0, 0, 0, 0, 0, 0),
                                       data: nil,
                                       data_type: .float,
                                       table_data: nil,
                                       table_data_type: .float,
                                       data_scale: 1,
                                       data_bias: 0)

    var layer_params = BNNSLayerParametersBroadcastMatMul(alpha: 1,
                                                          beta: 0,
                                                          transA: false,
                                                          transB: false,
                                                          quadratic: false,
                                                          a_is_weights: false,
                                                          b_is_weights: true,
                                                          iA_desc: i_desc,
                                                          iB_desc: w_desc,
                                                          o_desc: o_desc)

    let filter = BNNSFilterCreateLayerBroadcastMatMul(&layer_params, nil)
    defer {
        BNNSFilterDestroy(filter)
    }

    var outputValues = [Float](repeating: -1,
                                 count: o_desc.size.0 * o_desc.size.1 * o_desc.size.2 * batchSize)

    BNNSFilterApplyBatch(filter, batchSize,
                         inputValues, i_desc.size.0 * i_desc.size.1 * i_desc.size.2,
                         &outputValues, o_desc.size.0 * o_desc.size.1 * o_desc.size.2)
}
```

On return, `outputValues` contains each element of the input values, multiplied by 2:

```
[ // Batch 0, channel 0.
  22.0, 42.0, 
  62.0, 82.0, 
  102.0, 122.0, 
  142.0, 162.0, 

  // Batch 0, channel 1.
  202.0, 402.0, 
  602.0, 802.0, 
  1002.0, 1202.0, 
  1402.0, 1602.0, 

  // Batch 0, channel 2.
  2002.0, 4002.0, 
  6002.0, 8002.0, 
  10002.0, 12002.0, 
  14002.0, 16002.0, 

  // Batch 1, channel 0.
  24.0, 44.0, 
  64.0, 84.0, 
  104.0, 124.0, 
  144.0, 164.0, 

  // Batch 1, channel 1.
  204.0, 404.0, 
  604.0, 804.0, 
  1004.0, 1204.0, 
  1404.0, 1604.0, 

  // Batch 1, channel 2.
  2004.0, 4004.0, 
  6004.0, 8004.0, 
  10004.0, 12004.0, 
  14004.0, 16004.0 ]
```

## See Also

### Matrix multiplication

func BNNSDirectApplyBroadcastMatMul(Bool, Bool, Float, UnsafePointer&lt;BNNSNDArrayDescriptor>, UnsafePointer&lt;BNNSNDArrayDescriptor>, UnsafePointer&lt;BNNSNDArrayDescriptor>, UnsafePointer&lt;BNNSFilterParameters>?)

Applies a broadcast matrix multiplication operation directly to two input matrices.

Deprecated

class BroadcastMatrixMultiplyLayer

A layer object that wraps a broadcast matrix multiply filter and manages its deinitialization.

Deprecated

struct BNNSLayerParametersBroadcastMatMul

A set of parameters that define a broadcast matrix multiply layer.

Deprecated

func BNNSMatMulWorkspaceSize(Bool, Bool, Float, UnsafePointer&lt;BNNSNDArrayDescriptor>, UnsafePointer&lt;BNNSNDArrayDescriptor>, UnsafePointer&lt;BNNSNDArrayDescriptor>, UnsafePointer&lt;BNNSFilterParameters>?) -> Int

Returns the workspace size that a matrix multiply operation requires.

Deprecated

func BNNSMatMul(Bool, Bool, Float, UnsafePointer&lt;BNNSNDArrayDescriptor>, UnsafePointer&lt;BNNSNDArrayDescriptor>, UnsafePointer&lt;BNNSNDArrayDescriptor>, UnsafeMutableRawPointer?, UnsafePointer&lt;BNNSFilterParameters>?) -> Int32

Applies a matrix multiplication operation directly to two input matrices.

Deprecated

static func applyMatrixMultiplication(inputA: BNNSNDArrayDescriptor, transposed: Bool, inputB: BNNSNDArrayDescriptor, transposed: Bool, output: BNNSNDArrayDescriptor, alpha: Float, workspace: UnsafeMutableRawBufferPointer?, filterParameters: BNNSFilterParameters?) throws

Performs a matrix multiplication operation directly on two input matrices.

Deprecated

static func matrixMultiplicationWorkspaceSize(inputA: BNNSNDArrayDescriptor, transposed: Bool, inputB: BNNSNDArrayDescriptor, transposed: Bool, output: BNNSNDArrayDescriptor, alpha: Float, filterParameters: BNNSFilterParameters?) -> Int?

Returns the workspace size that a matrix multiply operation requires.

Deprecated

