

- SpriteKit
- SKTexture
-  init(noiseMap:) 

Initializer

# init(noiseMap:)

Creates a texture from the specified noise map.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+

``` source
convenience init(noiseMap: GKNoiseMap)
```

## Parameters 

`noiseMap`  

The noise map object from which to generate a texture.

## Return Value

A new texture based on the contents of the noise map.

## Discussion

The GKNoiseMap class encapsulates the output of procedural noise generation and processing. You use noise sources (the GKNoiseSource class cluster), noise objects (the GKNoise class), and noise maps to generate, process, and combine styles of noise, then use this method to create a graphical representation of the noise for use as a texture image in your game. Noise textures can be useful for imitating natural phenomena such as clouds, stone surfaces, and wood grain. You can also use noise textures as normal maps to make surfaces appear more natural under lighting.

This method colorizes the generated texture using the gradientColors property of the GKNoise object from which the noise map was created. By default, that property specifies a simple grayscale ramp, but you can change it to create more colorful textures. When you use the init(componentNoises:selectionNoise:) method to combine noise objects, each component noise object keeps its original colors, and the selection noise determines which component noise’s colors appear in which areas of a generated texture.

The following Swift code shows how to create a texture based on Perlin noise:

```
let noiseSource = GKPerlinNoiseSource(frequency: 4,
                                      octaveCount: 3,
                                      persistence: 0.2,
                                      lacunarity: 1,
                                      seed: 0)

let noise = GKNoise(noiseSource)

let noiseMap = GKNoiseMap(noise, size: double2(8,8),
                          origin: double2(0,0),
                          sampleCount: int2(640,640),
                          seamless: false)

let noiseTexture = SKTexture(noiseMap: noiseMap)
```

The following image illustrates a sprite node using this texture as both arguments for init(texture:normalMap:).

