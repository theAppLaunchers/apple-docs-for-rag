

- MapKit JS
- AnnotationCalloutDelegate
-  calloutLeftAccessoryForAnnotation 

Instance Method

# calloutLeftAccessoryForAnnotation

Returns an element to use as a custom accessory on the left side of the callout content area.

MapKit JS 5.0+

``` source
Element calloutLeftAccessoryForAnnotation(
 mapkit.Annotation annotation
);
```

## Parameters 

`annotation`  

The annotation for the callout.

## Return Value

This method returns a DOM element to display as the left accessory.

## Discussion

You use this method to provide a custom accessory for the left side of the callout content area (that the title and subtitle occupy).

Use CSS padding and margins to adjust the layout of accessory elements. An accessory element that’s shorter than the callout’s other content centers vertically in the callout. The accessory’s container doesn’t have padding, so a background that you set for an accessory element fully bleeds to the border of the callout. The callout does clip its content, so any background doesn’t won’t bleed outside the rounded corners of the callout.

MapKit JS ignores this method if you implement calloutElementForAnnotation. In that case, you’re responsible for the entirety of the callout.

Note that callouts are language-aware, *left* and *right* refer to the placement of the accessories in a left-to-right language. If the language property indicates a right-to-left language like Hebrew, the system mirrors the UI and the system places the left accessory on the right-hand side, and vice versa.

## See Also

### Providing elements

calloutContentForAnnotation

Returns custom content for the callout bubble.

calloutElementForAnnotation

Returns an element representing a custom callout.

calloutRightAccessoryForAnnotation

Returns an element to use as a custom accessory on the right side of the callout content area.

