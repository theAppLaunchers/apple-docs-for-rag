

- Accelerate
- BNNS
- BNNS.FusedFullyConnectedNormalizationLayer
-  init(input:output:fullyConnectedWeights:fullyConnectedBias:normalization:normalizationBeta:normalizationGamma:normalizationMomentum:normalizationEpsilon:normalizationActivation:filterParameters:) Deprecated

Initializer

# init(input:output:fullyConnectedWeights:fullyConnectedBias:normalization:normalizationBeta:normalizationGamma:normalizationMomentum:normalizationEpsilon:normalizationActivation:filterParameters:)

Returns a new fused, fully connected normalization layer.

iOS 14.0+iPadOS 14.0+Mac CatalystmacOS 11.0+tvOS 14.0+visionOSwatchOS 7.0+

``` source
convenience init?(
    input: BNNSNDArrayDescriptor,
    output: BNNSNDArrayDescriptor,
    fullyConnectedWeights: BNNSNDArrayDescriptor,
    fullyConnectedBias: BNNSNDArrayDescriptor?,
    normalization: BNNS.NormalizationType,
    normalizationBeta: BNNSNDArrayDescriptor,
    normalizationGamma: BNNSNDArrayDescriptor,
    normalizationMomentum: Float,
    normalizationEpsilon: Float,
    normalizationActivation: BNNS.ActivationFunction,
    filterParameters: BNNSFilterParameters? = nil
)
```

Deprecated

Use the BNNSGraph API instead.

## Parameters 

`input`  

The descriptor of the input.

`output`  

The descriptor of the output.

`fullyConnectedWeights`  

The descriptor of the fully connected weights.

`fullyConnectedBias`  

The descriptor of the fully connected bias.

`normalization`  

An enumeration that specifies the normalization type.

`normalizationBeta`  

The descriptor of the normalization beta.

`normalizationGamma`  

The descriptor of the normalization gamma.

`normalizationMomentum`  

A value between 0 and 1 that the normalization operation uses to update the moving mean and moving variance during training.

`normalizationEpsilon`  

The epsilon in the computation of the standard deviation.

`normalizationActivation`  

The activation function that the layer applies to the output.

`filterParameters`  

The runtime filter parameters.

