

- MapKit
- MKAnnotationView
-  isHighlighted 

Instance Property

# isHighlighted

A Boolean value that indicates whether the map view highlights the annotation view.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.2+visionOS 1.0+

``` source
@MainActor
var isHighlighted: Bool { get set }
```

## Discussion

Don’t set the value of this property directly. The map view sets it in response to touch events entering or exiting the annotation view’s bounds.

## See Also

### Getting and setting attributes

var isEnabled: Bool

A Boolean value that indicates whether the annotation is in an enabled state.

var image: UIImage?

The image the annotation view displays.

var annotation: (any MKAnnotation)?

The annotation object associated with the view.

var centerOffset: CGPoint

The offset (in points) at which to display the view.

var calloutOffset: CGPoint

The offset (in points) at which to place the callout.

var reuseIdentifier: String?

The string that identifies that the annotation view is reusable.

