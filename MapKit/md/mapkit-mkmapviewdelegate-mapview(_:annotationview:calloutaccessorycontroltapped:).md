

- MapKit
- MKMapViewDelegate
-  mapView(\_:annotationView:calloutAccessoryControlTapped:) 

Instance Method

# mapView(\_:annotationView:calloutAccessoryControlTapped:)

Tells the delegate when the user taps one of the annotation view’s accessory buttons.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
optional func mapView(
    _ mapView: MKMapView,
    annotationView view: MKAnnotationView,
    calloutAccessoryControlTapped control: UIControl
)
```

## Parameters 

`mapView`  

The map view containing the specified annotation view.

`view`  

The annotation view with the button that the person taps.

`control`  

The control that the person taps.

## Discussion

Accessory views contain custom content and the map view positions it on either side of the annotation title text. If a view you specify is a descendant of the UIControl class, the map view calls this method as a convenience whenever the user taps your view. You can use this method to respond to taps and perform any actions associated with that control. For example, if your control displays additional information about the annotation, you can use this method to present a modal panel with that information.

If your custom accessory views aren’t descendants of the UIControl class, the map view doesn’t call this method.

## See Also

### Managing annotation views

func mapView(MKMapView, viewFor: any MKAnnotation) -> MKAnnotationView?

Returns the view associated with the specified annotation object.

func mapView(MKMapView, didAdd: [MKAnnotationView])

Tells the delegate when the map view adds one or more annotation views to the map.

func mapView(MKMapView, clusterAnnotationForMemberAnnotations: [any MKAnnotation]) -> MKClusterAnnotation

Asks the delegate to provide a cluster annotation object for the specified annotations.

