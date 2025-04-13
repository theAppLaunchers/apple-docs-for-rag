

- UIKit
- UIView
-  effectiveUserInterfaceLayoutDirection 

Instance Property

# effectiveUserInterfaceLayoutDirection

The user interface layout direction appropriate for arranging the immediate content of the view.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
@MainActor
var effectiveUserInterfaceLayoutDirection: UIUserInterfaceLayoutDirection { get }
```

## Discussion

When a view’s immediate content is being arranged or drawn, you should always consult the value of this property. In addition, note that you can’t assume that the value propagates through the view’s subtree.

## See Also

### Adjusting the user interface

var overrideUserInterfaceStyle: UIUserInterfaceStyle

The user interface style adopted by the view and all of its subviews.

var semanticContentAttribute: UISemanticContentAttribute

A semantic description of the view’s contents, used to determine whether the view should be flipped when switching between left-to-right and right-to-left layouts.

class func userInterfaceLayoutDirection(for: UISemanticContentAttribute) -> UIUserInterfaceLayoutDirection

Returns the user interface direction for the given semantic content attribute.

class func userInterfaceLayoutDirection(for: UISemanticContentAttribute, relativeTo: UIUserInterfaceLayoutDirection) -> UIUserInterfaceLayoutDirection

Returns the layout direction implied by the specified semantic content attribute, relative to the specified layout direction.

