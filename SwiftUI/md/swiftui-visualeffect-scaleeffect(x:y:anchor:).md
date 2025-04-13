

- SwiftUI
- VisualEffect
-  scaleEffect(x:y:anchor:) 

Instance Method

# scaleEffect(x:y:anchor:)

Scales the view’s rendered output by the given horizontal and vertical amounts, relative to an anchor point.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
func scaleEffect(
    x: CGFloat = 1.0,
    y: CGFloat = 1.0,
    anchor: UnitPoint = .center
) -> some VisualEffect
```

## Parameters 

`x`  

An amount that represents the horizontal amount to scale the view. The default value is `1.0`.

`y`  

An amount that represents the vertical amount to scale the view. The default value is `1.0`.

`anchor`  

The point with a default of center that defines the location within the view from which to apply the transformation.

## Return Value

An effect that scales the view’s rendered output.

## See Also

### Scaling

func scaleEffect(_:anchor:)

Scales this view uniformly by the specified factor.

func scaleEffect(x: CGFloat, y: CGFloat, z: CGFloat, anchor: UnitPoint3D) -> some VisualEffect

Scales this view by the specified horizontal, vertical, and depth factors.

