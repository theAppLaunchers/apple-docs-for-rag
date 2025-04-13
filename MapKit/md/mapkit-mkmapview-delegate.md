

- MapKit
- MKMapView
-  delegate 

Instance Property

# delegate

The receiver’s delegate.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.2+visionOS 1.0+

``` source
@IBOutlet @MainActor
weak var delegate: (any MKMapViewDelegate)? { get set }
```

## Discussion

A map view sends messages to its delegate regarding the loading of map data and changes in the portion of the map it displays. The delegate also manages the annotation views that highlight points of interest on the map.

The delegate needs to implement the methods of the MKMapViewDelegate protocol.

## See Also

### Customizing the map view behavior

protocol MKMapViewDelegate

Optional methods that you use to receive map-related update messages.

