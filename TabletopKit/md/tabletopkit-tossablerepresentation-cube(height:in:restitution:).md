

- TabletopKit
- TossableRepresentation
-  cube(height:in:restitution:) 

Type Method

# cube(height:in:restitution:)

Creates a cube that the player tosses during gameplay.

visionOS 2.0+

``` source
static func cube(
    height: Float,
    in unit: UnitLength = .meters,
    restitution: Float? = nil
) -> TossableRepresentation
```

## Parameters 

`height`  

The height of the cube.

`unit`  

The unit of measurement for the height.

`restitution`  

The coefficient of restitution, in the range \[0, 1\].

## Discussion

The vertices for the simulated cube are oriented with faces axis aligned. In this orientation, the height (h) is measured from face to opposing face, and the vertices have the following coordinates, which all lie on a circumscribed sphere of radius r = h/2 ⋅ sqrt(3): { ±1, ±1, ±1 } ⋅ h/2 = { ±sqrt(3)/3, ±sqrt(3)/3, ±sqrt(3)/3 } ⋅ r

Higher restitution values indicate materials that conserve kinetic energy during collisions, causing objects to bounce off each other elastically. Lower values suggest materials that absorb kinetic energy, resulting in less bounce and more energy loss upon impact.

## See Also

### Creating geometric shapes

static func decahedron(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a decahedron, a symmetrical, ten-faced polyhedron with kite-shaped faces, that the player tosses during gameplay.

static func dodecahedron(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a regular dodecahedron, a shape with 12 pentagonal faces, that the player tosses during gameplay.

static func icosahedron(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a regular icosahedron, a shape with 20 triangular faces, that the player tosses during gameplay.

static func octahedron(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a regular octahedron, a shape with 8 triangular faces, that the player tosses during gameplay.

static func sphere(radius: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a sphere with the specified radius that the player tosses during gameplay.

static func tetrahedron(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a regular tetrahedron, a pyramid with four triangular faces, that the player tosses during gameplay.

