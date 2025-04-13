

- Model I/O
- MDLLightProbeIrradianceDataSource
-  sphericalHarmonicsCoefficients(atPosition:) 

Instance Method

# sphericalHarmonicsCoefficients(atPosition:)

Asks the data source to provide spherical harmonics coefficients that describe lighting conditions in all directions from the specified point in a scene.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+

``` source
optional func sphericalHarmonicsCoefficients(atPosition position: vector_float3) -> Data
```

## Parameters 

`position`  

The position for which lighting information is requested.

## Discussion

When you call the MDLAsset placeLightProbes(withDensity:heuristic:using:) method to automatically distribute light probes in a scene, Model I/O repeatedly calls this method to evaluate the lighting conditions at various points in the scene (as determined by the `density` and `heuristic` parameters), then uses the resulting information to choose where to place light probes.

The data you return from this method is equivalent to that provided by the sphericalHarmonicsCoefficients property of an existing light probe object. You provide this information in a data object containing an array of 32-bit floating-point values, organized into three noninterleaved data sets corresponding to the red, green, and blue sets of coefficients. The value you return for the sphericalHarmonicsLevel property determines the expected length of the array:

- At level 0, the array has 1 coefficient (3 values).

- At level 1, the array has 4 coefficients (3 sets of 4 values, 12 values total).

- At level 2, the array has 9 coefficients (3 sets of 9 values, 27 values total).

- At level 3, the array has 16 coefficients (3 sets of 16 values, 48 values total).

- Spherical harmonics levels beyond 3 are not supported.

## See Also

### Providing Light Probe Information

var boundingBox: MDLAxisAlignedBoundingBox

The bounding region of the scene to which light probes are being added.

**Required**

var sphericalHarmonicsLevel: Int

The number of levels of spherical harmonics information provided by the data source.

