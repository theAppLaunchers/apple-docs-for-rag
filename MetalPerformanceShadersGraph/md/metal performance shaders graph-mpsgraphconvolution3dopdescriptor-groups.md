

- Metal Performance Shaders Graph
- MPSGraphConvolution3DOpDescriptor
-  groups 

Instance Property

# groups

The number of partitions of the input and output channels.

iOS 16.3+iPadOS 16.3+Mac Catalyst 16.3+macOS 13.2+tvOS 16.3+visionOS 1.0+

``` source
var groups: Int { get set }
```

## Discussion

The convolution operation divides input and output channels in `groups` partitions. input channels in a group or partition are only connected to output channels in corresponding group. Number of weights the convolution needs is `outputFeatureChannels x inputFeatureChannels/groups x kernelDepth x kernelWidth x kernelHeight`

