

- UIKit
- UIPreviewParameters
-  visiblePath 

Instance Property

# visiblePath

The portion of the view to show in the preview.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 17.0+visionOS 1.0+

``` source
@NSCopying @MainActor
var visiblePath: UIBezierPath? { get set }
```

## Discussion

Specify the path information in the coordinate space of the view being animated.

## See Also

### Configuring the preview attributes

var backgroundColor: UIColor!

The background color to display behind the preview.

var shadowPath: UIBezierPath?

The path to use for drawing the preview’s shadow.

