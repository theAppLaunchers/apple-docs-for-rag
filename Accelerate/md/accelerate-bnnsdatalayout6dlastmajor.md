

- Accelerate
-  BNNSDataLayout6DLastMajor 

Global Variable

# BNNSDataLayout6DLastMajor

A constant that represents a 6D last-major tensor.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
var BNNSDataLayout6DLastMajor: BNNSDataLayout { get }
```

## Discussion

The value `(i, j, k, l, m, n)` is at index:

`i * stride[0] + j * stride[1] + k * stride[2] + l * stride[3] +`

`m * stride[4] + n * stride[5]`.

- `size[0]` is the size of the first dimension (`i`).

- `size[1]` is the size of the second dimension (`j`).

- `size[2]` is the size of the third dimension (`k`).

- `size[3]` is the size of the fourth dimension (`l`).

- `size[4]` is the size of the fifth dimension (`m`).

- `size[5]` is the size of the sixth dimension (`n`).

## See Also

### 6D Data Layouts

var BNNSDataLayout6DFirstMajor: BNNSDataLayout

A constant that represents a 6D first-major tensor.

