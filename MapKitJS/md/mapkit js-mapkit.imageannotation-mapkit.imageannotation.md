

- MapKit JS
- mapkit.ImageAnnotation
-  mapkit.ImageAnnotation 

Initializer

# mapkit.ImageAnnotation

Creates an image annotation with a URL to its image and a coordinate.

MapKit JS 5.0+

``` source
new mapkit.ImageAnnotation(
 mapkit.Coordinate|Place location,
 optional ImageAnnotationConstructorOptions options
);
```

## Parameters 

`location`  

The coordinate where this annotation appears.

`options`  

A hash of properties that initialize the annotation. The `options` hash needs to include url. MapKit JS displays an optional `title` and `subtitle` in a callout if they’re present.

## Discussion

This example shows two image annotations: one with a minimally defined image, and one with more options filled in:

```
var coordinate = new mapkit.Coordinate(38.897957, -77.036560);

// The house logo is a white square.
// The image size is 32 x 32. Becuase the default anchor point is the bottom center
// of the image, offset the anchor by (0, -16) to make the center of the
// image the anchor point.
var houseOptions = {
    title: "The White House",
    subtitle: "1600 Pennsylvania Ave NW",
    url: { 1: "/images/house.png", 2: "/images/house_2x.png"},
    anchorOffset: new DOMPoint(0, -16)
};
var houseAnnotation = new mapkit.ImageAnnotation(coordinate, houseOptions);
map.addAnnotation(houseAnnotation);

// This is how to implement a red pin.
var pinOptions = {
    url: {
        1: "/images/pin-red.png",
        2: "/images/pin-red_2x.png"
    }
};
var pinAnnotation = new mapkit.ImageAnnotation(coordinate, pinOptions);
map.addAnnotation(pinAnnotation);
```

## See Also

### Creating an image annotation

ImageAnnotationConstructorOptions

An object containing options for creating an image annotation.

