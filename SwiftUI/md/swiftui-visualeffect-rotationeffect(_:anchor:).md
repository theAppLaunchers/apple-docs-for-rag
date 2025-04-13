

- SwiftUI
- VisualEffect
-  rotationEffect(\_:anchor:) 

Instance Method

# rotationEffect(\_:anchor:)

Rotates content in two dimensions around the specified point.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
func rotationEffect(
    _ angle: Angle,
    anchor: UnitPoint = .center
) -> some VisualEffect
```

## Parameters 

`angle`  

The angle by which to rotate the content.

`anchor`  

A unit point within the content about which to perform the rotation. The default value is center.

## Return Value

A rotation effect.

## Discussion

This effect rotates the content around the axis that points out of the xy-plane. It has no effect on the content’s frame. The following code rotates text by 22˚ and then draws a border around the modified view to show that the frame remains unchanged by the rotation:

```
Text("Rotation by passing an angle in degrees")
    .visualEffect { content, geometryProxy in
        content
            .rotationEffect(.degrees(22))
    }
    .border(Color.gray)
```

## See Also

### Rotating

func rotation3DEffect(Angle, axis: (x: CGFloat, y: CGFloat, z: CGFloat), anchor: UnitPoint, anchorZ: CGFloat, perspective: CGFloat) -> some VisualEffect

Renders content as if it’s rotated in three dimensions around the specified axis.

func perspectiveRotationEffect(Angle, axis: (x: CGFloat, y: CGFloat, z: CGFloat), anchor: UnitPoint3D, perspective: CGFloat) -> some VisualEffect

Renders content as if it’s rotated in three dimensions around the specified axis.

func rotation3DEffect(Rotation3D, anchor: UnitPoint3D) -> some VisualEffect

Rotates content by the specified 3D rotation value.

func rotation3DEffect(_:axis:anchor:)

Rotates content by an angle about an axis that you specify as a tuple of elements.

