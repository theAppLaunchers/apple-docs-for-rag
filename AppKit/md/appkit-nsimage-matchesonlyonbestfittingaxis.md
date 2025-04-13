

- AppKit
- NSImage
-  matchesOnlyOnBestFittingAxis 

Instance Property

# matchesOnlyOnBestFittingAxis

A Boolean value that indicates whether the image matches only on the best fitting axis.

macOS 10.7+

``` source
var matchesOnlyOnBestFittingAxis: Bool { get set }
```

## Discussion

true if the image is drawn only on the best fitting axis; otherwise, false. This property defaults to false.

NSImage has always tried to use a representation with at least as many pixels as the destination rectangle. Many apps try to implement banners and 3 part / 9 part images by stretching an NSImage over a much larger area (usually only on a single axis).

With the addition of 2x assets these apps are finding this policy displays the 2x image rep when they would prefer the 1x rep. This behavior can be changed by using this method.

Note

It is still preferable to use the NSDrawThreePartImage(_:_:_:_:_:_:_:_:) and NSDrawNinePartImage(_:_:_:_:_:_:_:_:_:_:_:_:_:), functions when possible.

