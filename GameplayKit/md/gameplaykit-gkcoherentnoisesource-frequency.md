

- GameplayKit
- GKCoherentNoiseSource
-  frequency 

Instance Property

# frequency

A value that determines the size and spacing of features in generated noise.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+

``` source
var frequency: Double { get set }
```

## Discussion

The effect of this property varies for each coherent noise source class. Generally, increasing frequency increases the number of (and decreases the size of) visible features in any given unit area of a generated noise map. The default value is `1.0`.

Coherent noise is composed from several applications of a pseudorandom function. Each successive application, or *octave*, increases in frequency and decreases in amplitude relative to the previous octave. This combination of many octaves produces the fractal appearance that makes coherent noise resemble natural phenomena like clouds, stone, and water. This property controls the base frequency of the noise function; the octaveCount, lacunarity, and (for some subclasses) persistence properties determine how the frequencies of successive octaves change.

## See Also

### Managing Noise Generation Parameters

var octaveCount: Int

The number of octaves of the underlying noise function to use for generating noise.

var lacunarity: Double

The rate at which successive octaves of the noise function increase in frequency.

var seed: Int32

The value that determines the specific configuration of noise produced by the noise source.

