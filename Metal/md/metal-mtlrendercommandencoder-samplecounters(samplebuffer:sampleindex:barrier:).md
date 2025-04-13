

- Metal
- MTLRenderCommandEncoder
-  sampleCounters(sampleBuffer:sampleIndex:barrier:) 

Instance Method

# sampleCounters(sampleBuffer:sampleIndex:barrier:)

Encodes a command that samples hardware counters during the render pass and stores the data into a counter sample buffer.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 10.15+tvOS 14.0+visionOS 1.0+

``` source
func sampleCounters(
    sampleBuffer: any MTLCounterSampleBuffer,
    sampleIndex: Int,
    barrier: Bool
)
```

**Required**

## Parameters 

`sampleBuffer`  

An MTLCounterSampleBuffer instance that stores the GPU hardware data.

`sampleIndex`  

An index within `sampleBuffer` the command stores the data to.

`barrier`  

A Boolean value that indicates whether the command inserts a barrier before sampling the counter’s data.

A barrier ensures that the commands you encode before this one complete before the GPU samples the hardware counters, but can negatively impact runtime performance.

Running this command without a barrier means the GPU can sample counters concurrently with other commands from the encoder.

Either way, the `barrier` parameter for the command has no impact on sampling commands from other passes.

## Mentioned in 

Sampling GPU Data into Counter Sample Buffers

