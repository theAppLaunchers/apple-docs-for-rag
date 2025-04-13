

- AppKit
- NSStringDrawingContext
-  minimumScaleFactor 

Instance Property

# minimumScaleFactor

The scale factor that determines the smallest font size to use during drawing.

macOS 10.11+

``` source
var minimumScaleFactor: CGFloat { get set }
```

## Discussion

A value of `0.0` corresponds to a scale factor of `1.0`. Any value greater than `0.0` is multiplied by the font point size to get the smallest font size that is permissible to use. For example, 0.5 indicates a font that is half the size of the actual font, 0.75 is three-quarters of the font size, and so on. Typically, you specify a value between 0.0 and 1.0 to indicate how much the font can be shrunk during drawing.

The default value of this property is `0.0`.

## See Also

### Accessing the scale factors

var actualScaleFactor: CGFloat

The actual scale factor that the system applied to the font during drawing.

