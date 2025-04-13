

- Accelerate
- vImage_PerpsectiveTransform
-  init(a:b:c:d:tx:ty:vx:vy:v:) 

Initializer

# init(a:b:c:d:tx:ty:vx:vy:v:)

Creates a projective-transformation structure from the specified single-precision values.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
init(
    a: Float,
    b: Float,
    c: Float,
    d: Float,
    tx: Float,
    ty: Float,
    vx: Float,
    vy: Float,
    v: Float
)
```

## Parameters 

`a`  

The top-left cell in the 3 x 3 transformation matrix.

`b`  

The top-middle cell in the 3 x 3 transformation matrix.

`c`  

The middle-left cell in the 3 x 3 transformation matrix.

`d`  

The middle-middle cell in the 3 x 3 transformation matrix.

`tx`  

The x-coordinate translation.

`ty`  

The y-coordinate translation.

`vx`  

The x-component of the projective vector.

`vy`  

The y-component of the projective vector.

`v`  

The homogeneous scale factor.

## See Also

### Creating a projective-transformation structure

init()

Creates a projective-transformation structure.

init?(source: vImage_PerpsectiveTransform.QuadrilateralPoints, destination: vImage_PerpsectiveTransform.QuadrilateralPoints)

Returns a projective-transformation structure that defines the mapping between a source quadrilateral and a destination quadrilateral.

