

- UIKit
-  UICollectionViewFlowLayout 

Class

# UICollectionViewFlowLayout

A layout object that organizes items into a grid with optional header and footer views for each section.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
class UICollectionViewFlowLayout
```

## Overview

A flow layout is a type of collection view layout. Items in the collection view flow from one row or column (depending on the scrolling direction) to the next, with each row containing as many cells as will fit. Cells can be the same sizes or different sizes.

A flow layout works with the collection view’s delegate object to determine the size of items, headers, and footers in each section and grid. That delegate object must conform to the UICollectionViewDelegateFlowLayout protocol. Use of the delegate allows you to adjust layout information dynamically. For example, you use a delegate object to specify different sizes for items in the grid. If you don’t provide a delegate, the flow layout uses the default values you set in the properties of this class.

Flow layouts lay out their content using a fixed distance in one direction and a scrollable distance in the other. For example, in a vertically scrolling grid, the width of the grid content is constrained to the width of the corresponding collection view while the height of the content adjusts dynamically to match the number of sections and items in the grid. The layout scrolls vertically by default, but you can configure the scrolling direction using the scrollDirection property.

Each section in a flow layout can have its own custom header and footer. To configure the header or footer for a view, configure the size of the header or footer to be non-zero. Implement the appropriate delegate methods or assign appropriate values to the headerReferenceSize and footerReferenceSize properties. If the header or footer size is `0`, the corresponding view isn’t added to the collection view.

## Topics

### Configuring the flow layout

protocol UICollectionViewDelegateFlowLayout

The methods that let you coordinate with a flow layout object to implement a grid-based layout.

### Configuring the scroll direction

var scrollDirection: UICollectionView.ScrollDirection

The scroll direction of the grid.

enum ScrollDirection

Constants that indicate the direction of scrolling for the layout.

### Configuring item spacing

var minimumLineSpacing: CGFloat

The minimum spacing to use between lines of items in the grid.

var minimumInteritemSpacing: CGFloat

The minimum spacing to use between items in the same row.

var itemSize: CGSize

The default size to use for cells.

var estimatedItemSize: CGSize

The estimated size of cells in the collection view.

class let automaticSize: CGSize

A placeholder size for self-sizing cells.

var sectionInset: UIEdgeInsets

The margins used to lay out content in a section.

var sectionInsetReference: UICollectionViewFlowLayout.SectionInsetReference

The boundary that section insets are defined in relation to.

enum SectionInsetReference

Constants that describe the reference point of the section insets.

### Configuring headers and footers

var headerReferenceSize: CGSize

The default sizes to use for section headers.

var footerReferenceSize: CGSize

The default sizes to use for section footers.

Flow layout supplementary views

Constants that specify the types of supplementary views that can be presented using a flow layout.

### Pinning headers and footers

var sectionHeadersPinToVisibleBounds: Bool

A Boolean value that indicates whether headers pin to the top of the collection view bounds during scrolling.

var sectionFootersPinToVisibleBounds: Bool

A Boolean value that indicates whether footers pin to the bottom of the collection view bounds during scrolling.

## Relationships

### Inherits From

- UICollectionViewLayout

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol
- Sendable

## See Also

### Manual layouts

Customizing collection view layouts

Customize a view layout by changing the size of cells in the flow or implementing a mosaic style.

class UICollectionViewLayout

An abstract base class for generating layout information for a collection view.

class UICollectionViewTransitionLayout

A special type of layout object that lets you implement behaviors when changing from one layout to another in your collection view.

class UICollectionViewLayoutAttributes

A layout object that manages the layout-related attributes for a given item in a collection view.

class UICollectionViewFlowLayoutInvalidationContext

A set of properties for determining whether to recompute the size of items or their position in the layout.

