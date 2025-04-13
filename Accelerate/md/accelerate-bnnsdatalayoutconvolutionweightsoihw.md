

- Accelerate
-  BNNSDataLayoutConvolutionWeightsOIHW 

Global Variable

# BNNSDataLayoutConvolutionWeightsOIHW

A constant that represents a 4D array of convolution weights.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
var BNNSDataLayoutConvolutionWeightsOIHW: BNNSDataLayout { get }
```

## Discussion

The value `(kx ,ky, InChannel, OutChannel)` is at index:

`kx * stride[0] + ky * stride[1] + InChannel * stride[2] + OutChannel * stride[3]`.

- `size[0]` is the convolution kernel width in pixels.

- `size[1]` is the convolution kernel height in pixels.

- `size[2]` is the number of input channels.

- `size[3]` is the number of output channels.

## See Also

### 4D Data Layouts

var BNNSDataLayoutConvolutionWeightsIOHrWr: BNNSDataLayout

A constant that represents a 4D array of rotated convolution weights.

var BNNSDataLayoutConvolutionWeightsOIHrWr: BNNSDataLayout

A constant that represents a 4D array of rotated convolution weights.

var BNNSDataLayoutConvolutionWeightsOIHW_Pack32: BNNSDataLayout

A constant that represents a 4D array of packed convolution weights with 32-output channel packing and 128-byte array address alignment.

var BNNSDataLayout4DFirstMajor: BNNSDataLayout

A constant that represents a 4D first-major tensor.

var BNNSDataLayout4DLastMajor: BNNSDataLayout

A constant that represents a 4D last-major tensor.

