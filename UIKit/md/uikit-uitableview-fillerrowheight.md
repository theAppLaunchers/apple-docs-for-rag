

- UIKit
- UITableView
-  fillerRowHeight 

Instance Property

# fillerRowHeight

The height for empty rows that fill the table view.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

``` source
@MainActor
var fillerRowHeight: CGFloat { get set }
```

## Discussion

Table views with a style of UITableView.Style.plain can display filler rows, empty rows that appear below the last row when there isn’t enough content to fill the table view. Set this property to adjust the height of each filler row:

- Set `0.0` to not display filler rows. This behavior is the default in iOS 15 and later.

- Set automaticDimension to display filler rows that use an automatic height, matching the height of the last row in the table view. This behavior is the default in versions of iOS earlier than iOS 15.

- Set any other positive value to display filler rows of that specified height.

A table view with a style other than UITableView.Style.plain doesn’t show filler rows, so it ignores any value other than `0.0` for this property.

## See Also

### Configuring cell height and layout

var rowHeight: CGFloat

The default height in points of each row in the table view.

var estimatedRowHeight: CGFloat

The estimated height of rows in the table view.

var cellLayoutMarginsFollowReadableWidth: Bool

A Boolean value that indicates whether the cell margins derive from the width of the readable content guide.

var insetsContentViewsToSafeArea: Bool

A Boolean value that indicates whether the table view adjusts the content views of its cells, headers, and footers to fit within the safe area.

