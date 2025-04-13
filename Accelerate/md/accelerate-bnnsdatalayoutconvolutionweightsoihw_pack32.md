

- Accelerate
-  BNNSDataLayoutConvolutionWeightsOIHW_Pack32 

Global Variable

# BNNSDataLayoutConvolutionWeightsOIHW_Pack32

A constant that represents a 4D array of packed convolution weights with 32-output channel packing and 128-byte array address alignment.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
var BNNSDataLayoutConvolutionWeightsOIHW_Pack32: BNNSDataLayout { get }
```

## Discussion

The Value `(kx, ky, InChannel, OutChannel)` is at index:

`OutChannelPositionInGroup + kw * 32 + ky * kernel_width * 32 + InChannel * kernel_height * kernel_width * 32 + OutChannelGroup * input_channels * kernel_height * kernel_width * 32`

Where:

- `kernel_width` is the kernel width.

- `kernel_height` is the kernel height.

- `input_channels` is the number of input channels.

- `output_channels` is the number of output channels.

- `OutChannelGroup = OutChannel / 32`.

- `OutChannelPositionInGroup = OutChannel % 32`.

- `kw` is `size[0]` and `kx` is between `0` to `kw-1`.

- `kh` is `size[1]` and `ky` is between `0` to `kh-1`.

## See Also

### 4D Data Layouts

var BNNSDataLayoutConvolutionWeightsOIHW: BNNSDataLayout

A constant that represents a 4D array of convolution weights.

var BNNSDataLayoutConvolutionWeightsIOHrWr: BNNSDataLayout

A constant that represents a 4D array of rotated convolution weights.

var BNNSDataLayoutConvolutionWeightsOIHrWr: BNNSDataLayout

A constant that represents a 4D array of rotated convolution weights.

var BNNSDataLayout4DFirstMajor: BNNSDataLayout

A constant that represents a 4D first-major tensor.

var BNNSDataLayout4DLastMajor: BNNSDataLayout

A constant that represents a 4D last-major tensor.

