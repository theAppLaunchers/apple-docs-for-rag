

- Accelerate
- BNNSPoolingLayerParameters
-  init(x_stride:y_stride:x_padding:y_padding:k_width:k_height:in_channels:out_channels:pooling_function:bias:activation:) Deprecated

Initializer

# init(x_stride:y_stride:x_padding:y_padding:k_width:k_height:in_channels:out_channels:pooling_function:bias:activation:)

Returns a new pooling layer parameters structure

iOS 10.0–14.0DeprecatediPadOS 10.0–14.0DeprecatedMac Catalyst 13.1–14.0DeprecatedmacOS 10.12–11.0DeprecatedtvOS 10.0–14.0DeprecatedvisionOS 1.0–1.0DeprecatedwatchOS 3.0–7.0Deprecated

``` source
init(
    x_stride: Int,
    y_stride: Int,
    x_padding: Int,
    y_padding: Int,
    k_width: Int,
    k_height: Int,
    in_channels: Int,
    out_channels: Int,
    pooling_function: BNNSPoolingFunction,
    bias: BNNSLayerData,
    activation: BNNSActivation
)
```

## Parameters 

`x_stride`  

The X increment in the input image.

`y_stride`  

The Y increment in the input image.

`x_padding`  

The X padding.

`y_padding`  

The Y padding.

`k_width`  

The width of the convolution kernel.

`k_height`  

The height of the convolution kernel.

`in_channels`  

The number of input channels.

`out_channels`  

The number of output channels.

`pooling_function`  

The pooling function to apply to each sample

`bias`  

Layer bias, one for each output channel.

`activation`  

The layer activation function

## See Also

### Initializers

init()Deprecated

init(x_stride: Int, y_stride: Int, x_padding: Int, y_padding: Int, k_width: Int, k_height: Int, in_channels: Int, out_channels: Int, pooling_function: BNNSPoolingFunction)Deprecated

