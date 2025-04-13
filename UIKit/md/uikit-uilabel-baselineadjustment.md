

- UIKit
- UILabel
-  baselineAdjustment 

Instance Property

# baselineAdjustment

An option that controls whether the text’s baseline remains fixed when text needs to shrink to fit in the label.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
var baselineAdjustment: UIBaselineAdjustment { get set }
```

## Discussion

If adjustsFontSizeToFitWidth is true, this property controls the behavior of the text baselines in situations where the text needs the font size adjusted in order to fit. The default value of this property is UIBaselineAdjustment.alignBaselines. This property is effective only when the numberOfLines is `1`.

## See Also

### Sizing the label’s text

var adjustsFontSizeToFitWidth: Bool

A Boolean value that determines whether the label reduces the text’s font size to fit the title string into the label’s bounding rectangle.

var allowsDefaultTighteningForTruncation: Bool

A Boolean value that determines whether the label tightens text before truncating.

var minimumScaleFactor: CGFloat

The minimum scale factor for the label’s text.

var numberOfLines: Int

The maximum number of lines for rendering text.

var sizingRule: UILetterformAwareSizingRule

The typographic bounds-sizing behavior that handles text with fonts that contain oversize characters.

**Required**

