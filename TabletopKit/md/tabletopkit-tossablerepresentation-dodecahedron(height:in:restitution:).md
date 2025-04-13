

- TabletopKit
- TossableRepresentation
-  dodecahedron(height:in:restitution:) 

Type Method

# dodecahedron(height:in:restitution:)

Creates a regular dodecahedron, a shape with 12 pentagonal faces, that the player tosses during gameplay.

visionOS 2.0+

``` source
static func dodecahedron(
    height: Float,
    in unit: UnitLength = .meters,
    restitution: Float? = nil
) -> TossableRepresentation
```

## Parameters 

`height`  

The height of the dodecahedron.

`unit`  

The unit of measurement for the height.

`restitution`  

The coefficient of restitution, in the range \[0, 1\].

## Discussion

The vertices for the simulated dodecahedron are oriented with one face toward +y with one vertex of that top face oriented toward -z. In this orientation, the height (h) is measured from face to opposing face, and the vertices have the following coordinates, which all lie on a circumscribed sphere of radius r = h/2 ⋅ sqrt(15)/(phi ⋅ sqrt(phi^2 + 1)), where phi = (sqrt(5) + 1)/2: ±Y face: ±{ 0, +1, -2/phi^2 } ⋅ h/2, ±{+2/phi ⋅ sin(72º), +1, -2/phi^2 ⋅ cos(72º) } ⋅ h/2, ±{+2/phi ⋅ sin(36º), +1, +2/phi^2 ⋅ cos(36º) } ⋅ h/2, ±{-2/phi ⋅ sin(36º), +1, +2/phi^2 ⋅ cos(36º) } ⋅ h/2, ±{-2/phi ⋅ sin(72º), +1, -2/phi^2 ⋅ cos(72º) } ⋅ h/2 Equator: ±{ 0, +1/phi^3, -2/phi } ⋅ h/2, ±{+2/phi^2 ⋅ sin(72º), +1/phi^3, -2/phi ⋅ cos(72º) } ⋅ h/2, ±{+2/phi^2 ⋅ sin(36º), +1/phi^3, +2/phi ⋅ cos(36º) } ⋅ h/2, ±{-2/phi^2 ⋅ sin(36º), +1/phi^3, +2/phi ⋅ cos(36º) } ⋅ h/2, ±{-2/phi^2 ⋅ sin(72º), +1/phi^3, -2/phi ⋅ cos(72º) } ⋅ h/2

Higher restitution values indicate materials that conserve kinetic energy during collisions, causing objects to bounce off each other elastically. Lower values suggest materials that absorb kinetic energy, resulting in less bounce and more energy loss upon impact.

## See Also

### Creating geometric shapes

static func cube(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a cube that the player tosses during gameplay.

static func decahedron(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a decahedron, a symmetrical, ten-faced polyhedron with kite-shaped faces, that the player tosses during gameplay.

static func icosahedron(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a regular icosahedron, a shape with 20 triangular faces, that the player tosses during gameplay.

static func octahedron(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a regular octahedron, a shape with 8 triangular faces, that the player tosses during gameplay.

static func sphere(radius: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a sphere with the specified radius that the player tosses during gameplay.

static func tetrahedron(height: Float, in: UnitLength, restitution: Float?) -> TossableRepresentation

Creates a regular tetrahedron, a pyramid with four triangular faces, that the player tosses during gameplay.

