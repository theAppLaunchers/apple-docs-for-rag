

- Game Controller
- GCDualSenseAdaptiveTrigger
- GCDualSenseAdaptiveTrigger.PositionalAmplitudes
-  init(values:) 

Initializer

# init(values:)

Creates a positional amplitudes structure with the specified amplitude values.

iOS 15.4+iPadOS 15.4+Mac Catalyst 15.4+macOS 12.3+tvOS 15.4+visionOS 1.0+

``` source
init(values: (Float, Float, Float, Float, Float, Float, Float, Float, Float, Float))
```

## Parameters 

`values`  

The amplitude values for possible trigger positions. Each value is between `0` and `1`, where `0` is the minimum and `1` is the maximum amplitude.

## See Also

### Creating multiple amplitudes

init()

Creates an empty positional amplitudes structure.

