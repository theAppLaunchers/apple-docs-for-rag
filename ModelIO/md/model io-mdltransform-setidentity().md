

- Model I/O
- MDLTransform
-  setIdentity() 

Instance Method

# setIdentity()

Sets all factors of the transform to those of the identity transformation.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
func setIdentity()
```

## Discussion

The identity transform is equivalent to the lack of a transformation, so an object affected by the transform uses the same coordinate space as its parent. Calling this method also erases any time-sampled data, creating a static transform.

## See Also

### Using Factors of a Static Transform

var translation: vector_float3

The x-, y-, and z-axis offsets of the transform relative to its parent coordinate space.

var rotation: vector_float3

The orientation, as a vector of Euler angles in radians, of the transform relative to its parent coordinate space.

var scale: vector_float3

The x-, y-, and z-axis scale factors of the transform relative to its parent coordinate space.

var shear: vector_float3

The x-, y-, and z-axis shear factors of the transform relative to its parent coordinate space.

