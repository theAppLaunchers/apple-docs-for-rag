

- UIKit
- NSCollectionLayoutDimension
-  uniformAcrossSiblings(estimate:) 

Type Method

# uniformAcrossSiblings(estimate:)

Creates a dimension in which each item receives as much room as it requires and grows to match the dimension of its largest sibling.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+tvOS 17.0+visionOS 1.0+

``` source
@MainActor
class func uniformAcrossSiblings(estimate estimatedDimension: CGFloat) -> Self
```

## Discussion

Use the uniformAcrossSiblings(estimate:) dimension to ensure that self-sizing items have a consistent size across their group. This dimension provides an alternative to using the estimated(_:) dimension, which might not result in a uniform layout for items that vary in size.

Items with this dimension receive at least as much room as they require, and they increase in size to match the dimension of the largest self-sizing sibling in their parent group. The parent group’s dimension needs to be estimated(_:) on the axis where items specify this dimension so the group can grow to fit the items.

For example, items using this dimension in a horizontal NSCollectionLayoutGroup all have a height equal to the tallest item in that group. That group’s heightDimension is estimated(_:) to allow for it to grow to fit the tallest item. The following code shows an example of this layout.

```
// Item width: To lay out 3 items horizontally, use 1/3 of the width of the group.
// Item height: To achieve a consistent height for the items, use `uniformAcrossSiblings(estimate:)`.
let itemCount = 3
let itemSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0 / CGFloat(itemCount)),
                                      heightDimension: .uniformAcrossSiblings(estimate: 50))
let item = NSCollectionLayoutItem(layoutSize: itemSize)

// Group width: To use the entire horizontal width of the section, use the full fractional width.
// Group height: To allow the group's height to grow for the items, use `estimated(_:)`.
let groupSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                       heightDimension: .estimated(50))
let group = NSCollectionLayoutGroup.horizontal(layoutSize: groupSize,
                                               repeatingSubitem: item,
                                               count: itemCount)

let section = NSCollectionLayoutSection(group: group)
```

Important

If you use a uniformAcrossSiblings(estimate:) dimension on the outermost group in a section, the size of the largest item in that group applies across the entire section, including nested groups.

Only use this dimension in layouts where the number of items is relatively small. To compute the size for this type of dimension, the layout needs to retrieve attributes for all siblings in the parent group, so the performance is linear to the number of items in the group.

Related sessions from WWDC23

Session 10055: What’s new in UIKit

## See Also

### Creating a dimension

class func absolute(CGFloat) -> Self

Creates a dimension with an absolute point value.

class func estimated(CGFloat) -> Self

Creates a dimension with an estimated point value.

class func fractionalHeight(CGFloat) -> Self

Creates a dimension that is computed as a fraction of the height of the containing group.

class func fractionalWidth(CGFloat) -> Self

Creates a dimension that is computed as a fraction of the width of the containing group.

