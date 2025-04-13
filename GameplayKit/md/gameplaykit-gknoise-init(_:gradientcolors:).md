

- GameplayKit
- GKNoise
-  init(\_:gradientColors:) 

Initializer

# init(\_:gradientColors:)

Initializes a noise object with the specified noise source, with colors for later use in generating noise textures.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+

**macOS**

``` source
init(
    _ noiseSource: GKNoiseSource,
    gradientColors: [NSNumber : NSColor]
)
```

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS**

``` source
init(
    _ noiseSource: GKNoiseSource,
    gradientColors: [NSNumber : UIColor]
)
```

## Parameters 

`noiseSource`  

The noise source defining the style and configuration of noise to generate.

`gradientColors`  

A dictionary that specifies a gradient ramp for colorizing generated noise. Each key in this dictionary specifies a value in the generated noise field, and the corresponding value for that key is the color to associate with that noise value when generating textures or images from the noise field. For more details, see the gradientColors property.

## Return Value

A new noise object.

## Discussion

To sample from the newly created object’s noise field or generate texture images, create a GKNoiseMap object from this noise object. Optionally, before doing so you can apply operations to process or transform the noise field, or combine it with other noise objects, to create a more complex or natural noise pattern. For details, see Applying Operations to Noise Values, Applying Operations that Combine Noise, Applying Operations that Distort Noise, Applying Geometric Transformations, and Creating Noise by Combining Noise in GKNoise.

The `gradientColors` parameter specifies a color ramp as metadata to accompany the noise object. When you later create a GKNoiseMap object from this noise object and use the init(noiseMap:) method to generate a texture image from the noise map, the SKTexture class automatically uses the gradient colors from the noise map’s underlying noise objects. If you combine noise objects using the init(componentNoises:selectionNoise:) method before generating a noise map, texture generation automatically uses the color gradient corresponding to each component noise for the regions of the noise map where that noise appears.

## See Also

### Creating Noise

convenience init(GKNoiseSource)

Initializes a noise object with the specified noise source.

