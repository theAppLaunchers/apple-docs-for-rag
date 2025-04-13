

- Metal Performance Shaders Graph
- MPSGraphDepthwiseConvolution3DOpDescriptor
-  channelDimensionIndex 

Instance Property

# channelDimensionIndex

The axis that contains the channels in the input and the weights, within the 4D tile of the last dimensions.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

``` source
var channelDimensionIndex: Int { get set }
```

## Discussion

For example the value of `-1` corresponds to `NDHWC`, `NHWC` layouts. This allows the placement of the channel index anywhere within the last 4 dimensions of the tensor. In case your weights are in a different layout you can bring them to the same layout as inputs using transposes or permutations. Default value: `-4`, corresponds to `NCDHW` and `CDHW` layouts.

