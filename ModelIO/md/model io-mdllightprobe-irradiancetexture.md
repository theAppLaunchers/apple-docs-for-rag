

- Model I/O
- MDLLightProbe
-  irradianceTexture 

Instance Property

# irradianceTexture

A cube map texture that contains samples of the total light arriving at the light probe’s position from every direction.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var irradianceTexture: MDLTexture? { get }
```

## Discussion

A renderer can use this texture to create diffuse lighting effects. You can derive an irradiance map from a reflective texture with methods on the MDLTexture class, or when creating a light probe with the init(textureSize:forLocation:lightsToConsider:objectsToConsider:reflectiveCubemap:irradianceCubemap:) method.

For example, consider a light probe whose reflective texture is red in all directions above the probe’s location and blue in all directions below that point. A diffuse material on the side of such an object should appear purple, because the side of the object receives a blend of the red light from above and the blue light from below. Therefore, the irradiance texture for this light probe is red directly above, blue directly below, and contains gradations of purple on all sides.

## See Also

### Working with Textures

var reflectiveTexture: MDLTexture?

A cube map texture that contains a rendering of a scene as seen from the light probe’s position.

