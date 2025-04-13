

- MapKit
- MKAnnotationView
-  annotation 

Instance Property

# annotation

The annotation object associated with the view.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.2+visionOS 1.0+

``` source
@MainActor
var annotation: (any MKAnnotation)? { get set }
```

## Discussion

Don’t change the value of this property directly. This property contains a non-`nil` value only while the annotation view is visible on the map. If the map view queues this annotation view and is waiting to reuse it, the value is `nil`.

## See Also

### Getting and setting attributes

var isEnabled: Bool

A Boolean value that indicates whether the annotation is in an enabled state.

var image: UIImage?

The image the annotation view displays.

var isHighlighted: Bool

A Boolean value that indicates whether the map view highlights the annotation view.

var centerOffset: CGPoint

The offset (in points) at which to display the view.

var calloutOffset: CGPoint

The offset (in points) at which to place the callout.

var reuseIdentifier: String?

The string that identifies that the annotation view is reusable.

