

- MapKit
- MKMapSnapshotter
- MKMapSnapshotter.Options
-  appearance 

Instance Property

# appearance

The visual style (light or dark) to apply to the map when rendering the snapshot image.

macOS 10.14+

``` source
var appearance: NSAppearance? { get set }
```

## Discussion

Use this property to specify a light or dark appearance for the map in the resulting snapshot image. When the value of this property is `nil` (the default), the snapshotter derives the appropriate appearance based on the following logic:

- If the user specifically disables Dark Mode for map content in the Maps app, the snapshot uses a light appearance.

- The snapshot uses your app’s appearance.

- The snapshot uses the system appearance.

## See Also

### Configuring the image output

var traitCollection: UITraitCollection

Traits that determine the appearance of the map snapshot.

var size: CGSize

The size of the image that you want to create.

var scale: CGFloat

The scale factor to use when creating the image.

Deprecated

