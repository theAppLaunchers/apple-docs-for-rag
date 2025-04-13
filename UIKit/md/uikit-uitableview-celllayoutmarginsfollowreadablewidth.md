

- UIKit
- UITableView
-  cellLayoutMarginsFollowReadableWidth 

Instance Property

# cellLayoutMarginsFollowReadableWidth

A Boolean value that indicates whether the cell margins derive from the width of the readable content guide.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
var cellLayoutMarginsFollowReadableWidth: Bool { get set }
```

## See Also

### Related Documentation

var readableContentGuide: UILayoutGuide

A layout guide representing an area with a readable width within the view.

### Configuring cell height and layout

var rowHeight: CGFloat

The default height in points of each row in the table view.

var estimatedRowHeight: CGFloat

The estimated height of rows in the table view.

var fillerRowHeight: CGFloat

The height for empty rows that fill the table view.

var insetsContentViewsToSafeArea: Bool

A Boolean value that indicates whether the table view adjusts the content views of its cells, headers, and footers to fit within the safe area.

