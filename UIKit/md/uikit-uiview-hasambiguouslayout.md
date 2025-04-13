

- UIKit
- UIView
-  hasAmbiguousLayout 

Instance Property

# hasAmbiguousLayout

A Boolean value that determines whether the constraints impacting the layout of the view incompletely specify the location of the view.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
var hasAmbiguousLayout: Bool { get }
```

## Discussion

The value of this property is true if the view’s location is incompletely specified, false otherwise.

If there aren’t enough constraints in the system to uniquely determine layout, the layout is considered ambiguous. For example, if the only constraint in the system is `x = y + 100`, the layout is ambiguous because there are many possible values for `x` and `y`. UIKit does not automatically detect every ambiguous layout, so you may need to look for symptoms of ambiguity, such as views that jump from place to place, or that are in the wrong place.

This property should only be used for debugging constraint-based layout. No app should ship with usage of this property as part of its operation.

## See Also

### Debugging Auto Layout

func constraintsAffectingLayout(for: NSLayoutConstraint.Axis) -> [NSLayoutConstraint]

Returns the constraints impacting the layout of the view for a given axis.

func exerciseAmbiguityInLayout()

Randomly changes the frame of a view with an ambiguous layout between the different valid values.

