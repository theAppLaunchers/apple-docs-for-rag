

- MapKit JS
- StyleConstructorOptions
-  lineDash 

Instance Property

# lineDash

An array of line and gap lengths for creating a dashed line.

MapKit JS 5.0+

``` source
attribute number[] lineDash;
```

## Discussion

This property provides an array to use as the line’s dash pattern where the numbers represent line and gap lengths in CSS pixels. For example, `[10, 5]` means draw for 10 pixels, leave a 5-pixel gap, then repeat. If there’s an odd number of elements in the array, MapKit JS copies and duplicates it. Set to an empty array (`[]`), to draw solid lines. The default line dash array is `[]`.

## See Also

### Setting line styles

lineCap

The style to use when drawing line endings.

lineDashOffset

The number of CSS pixels to use as the offset when drawing a line’s dash pattern.

lineJoin

The style to use when drawing joins between line segments.

lineWidth

The width of a line’s stroke, in CSS pixels.

