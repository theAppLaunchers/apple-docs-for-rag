

- MapKit JS
- AnnotationCalloutDelegate
-  calloutAnchorOffsetForAnnotation 

Instance Method

# calloutAnchorOffsetForAnnotation

Returns a point determining the callout’s anchor offset.

MapKit JS 5.0+

``` source
DOMPoint calloutAnchorOffsetForAnnotation(
 mapkit.Annotation annotation,
 Object size
);
```

## Parameters 

`annotation`  

The annotation for the callout.

`size`  

The width and height of the callout element, which MapKit JS determines.

## Return Value

The method returns a `DOMPoint` that you set as the callout’s `anchorOffset` property.

## Discussion

MapKit JS calls this method after calloutElementForAnnotation on the annotation’s callout delegate with `annotation` and `size` as parameters. The `size` parameter represents the size of the callout element, which MapKit JS determines. It’s an object with two number properties, `width` and `height`, and you can use them to compute the anchor offset.

Two offset values affect the position of the callout element:

- The calloutOffset property of the annotation, which is the offset of the callout element relative to the annotation element.

- The anchor offset, which is the offset of the callout relative to the annotation’s calloutOffset.

The default value for the callout’s `anchorOffset` is `(0, 0)`, which means that the bottom center of the callout coincides with the callout offset of the selected annotation.

To choose a different offset, provide a `DOMPoint` where positive x-values move the element to the left, and positive y-values move the element up.

## See Also

### Customizing callout appearance

calloutShouldAppearForAnnotation

Determines whether the callout appears for an annotation.

calloutShouldAnimateForAnnotation

Determines whether the callout animates.

calloutAppearanceAnimationForAnnotation

Returns a CSS animation to use when the callout appears.

