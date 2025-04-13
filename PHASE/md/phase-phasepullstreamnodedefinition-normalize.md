

- PHASE
- PHASEPullStreamNodeDefinition
-  normalize 

Instance Property

# normalize

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
var normalize: Bool { get set }
```

## Discussion

```
@property normalize
@abstract Determines whether or not the engine should normalize the stream. The default value is NO.
@discussion
    In general, clients are advised to normalize the input. Normalization is required to properly calibrate the output level.
    If you set this value to NO, it's advised that you do custom normalization of the audio data prior to passing the buffers to PHASE.
```

