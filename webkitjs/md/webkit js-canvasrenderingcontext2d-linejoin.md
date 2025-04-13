

- WebKit JS
- CanvasRenderingContext2D
-  lineJoin 

Instance Property

# lineJoin

A string specifying the manner in which line joins are drawn.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
attribute DOMString lineJoin;
```

## Discussion

A join exists at any point in a subpath shared by two consecutive lines. When a subpath is closed, then a join also exists at its first point (equivalent to its last point) connecting the first and last lines in the subpath.

In addition to the point where the join occurs, two additional points are relevant to each join, one for each line: the two corners found half the line width away from the join point, one perpendicular to each line, each on the side furthest from the other line.

A filled triangle connecting these two opposite corners with a straight line, with the third point of the triangle being the join point, must be rendered at all joins. The `lineJoin` attribute controls whether anything else is rendered.

Possible values are `bevel` (default), `round`, and `miter`.

The `bevel` value means that this is all that is rendered at joins.

The `round` value means that a filled arc connecting the two aforementioned corners of the join, abutting (and not overlapping) the aforementioned triangle, with the diameter equal to the line width and the origin at the point of the join, must be rendered at joins.

The `miter` value means that a second filled triangle must (if it can given the miter length) be rendered at the join, with one line being the line between the two aforementioned corners, abutting the first triangle, and the other two being continuations of the outside edges of the two joining lines, as long as required to intersect without going over the miter length.

## See Also

### Filling and Stroking Lines and Paths

fill

Fills the current path using the current fill color, gradient, or pattern.

fillStyle

A CSS color, a gradient, or a pattern used to fill shapes and text.

lineCap

A string specifying the type of end cap to put on lines to be drawn using `lineTo()`.

lineWidth

A floating-point number that controls the width of lines and strokes, in pixels.

miterLimit

A floating-point number that controls the miter limit ratio for mitered line joins.

stroke

Draws the outline of the current path using the current stroke style and line width.

strokeStyle

A CSS color, a gradient, or a pattern used to stroke lines and shapes.

