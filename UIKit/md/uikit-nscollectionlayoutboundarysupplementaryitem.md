

- UIKit
-  NSCollectionLayoutBoundarySupplementaryItem 

Class

# NSCollectionLayoutBoundarySupplementaryItem

An object used to add headers or footers to a collection view.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
@MainActor
class NSCollectionLayoutBoundarySupplementaryItem
```

## Overview

A boundary supplementary item is a specialized type of supplementary item (NSCollectionLayoutSupplementaryItem). You use boundary supplementary items to add headers or footers to a section of a collection view or the entire collection view.

Each type of supplementary item must have a unique element kind. Consider tracking these strings together in a way that makes it straightforward to identify each element, for example:

- Swift
- Objective-C

```
struct ElementKind {
    static let badge = "badge-element-kind"
    static let background = "background-element-kind"
    static let sectionHeader = "section-header-element-kind"
    static let sectionFooter = "section-footer-element-kind"
    static let layoutHeader = "layout-header-element-kind"
    static let layoutFooter = "layout-footer-element-kind"
}
```

```
NSString* const ELEMENT_KIND_BADGE = @"badge-element-kind";
NSString* const ELEMENT_KIND_BACKGROUND = @"background-element-kind";
NSString* const ELEMENT_KIND_SECTION_HEADER = @"section-header-element-kind";
NSString* const ELEMENT_KIND_SECTION_FOOTER = @"section-footer-element-kind";
NSString* const ELEMENT_KIND_LAYOUT_HEADER = @"layout-header-element-kind";
NSString* const ELEMENT_KIND_LAYOUT_FOOTER = @"layout-footer-element-kind";
```

Add boundary supplementary items to a section by setting that section’s boundarySupplementaryItems property:

- Swift
- Objective-C

```
let section = NSCollectionLayoutSection(group: group)

let headerFooterSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                             heightDimension: .estimated(44))

let sectionHeader = NSCollectionLayoutBoundarySupplementaryItem(layoutSize: headerFooterSize,
                                                               elementKind: ElementKind.sectionHeader,
                                                                 alignment: .top)
let sectionFooter = NSCollectionLayoutBoundarySupplementaryItem(layoutSize: headerFooterSize,
                                                               elementKind: ElementKind.sectionFooter,
                                                                 alignment: .bottom)

section.boundarySupplementaryItems = [sectionHeader, sectionFooter]
```

```
NSCollectionLayoutSection *section = [NSCollectionLayoutSection sectionWithGroup:group];

NSCollectionLayoutSize *headerFooterSize = [NSCollectionLayoutSize sizeWithWidthDimension:[NSCollectionLayoutDimension fractionalWidthDimension:1.0] heightDimension:[NSCollectionLayoutDimension absoluteDimension:44.0]];

NSCollectionLayoutBoundarySupplementaryItem *sectionHeader = [NSCollectionLayoutBoundarySupplementaryItem boundarySupplementaryItemWithLayoutSize: headerFooterSize elementKind: ELEMENT_KIND_SECTION_HEADER alignment: NSRectAlignmentTop];

NSCollectionLayoutBoundarySupplementaryItem *sectionFooter = [NSCollectionLayoutBoundarySupplementaryItem boundarySupplementaryItemWithLayoutSize: headerFooterSize elementKind: ELEMENT_KIND_SECTION_FOOTER alignment: NSRectAlignmentBottom];

[section setBoundarySupplementaryItems: @[sectionHeader, sectionFooter]];
```

## Topics

### Creating a boundary supplementary item

convenience init(layoutSize: NSCollectionLayoutSize, elementKind: String, alignment: NSRectAlignment)

Creates a boundary supplementary item of the specified size and element kind, with an alignment relative to a section or layout.

convenience init(layoutSize: NSCollectionLayoutSize, elementKind: String, alignment: NSRectAlignment, absoluteOffset: CGPoint)

Creates a boundary supplementary item of the specified size and element kind, with an alignment relative to a section or layout at an absolute offset.

### Specifying scrolling behavior

var pinToVisibleBounds: Bool

A Boolean value that indicates whether a header or footer is pinned to the top or bottom visible boundary of the section or layout it’s attached to.

### Specifying position

var offset: CGPoint

The floating-point value of the boundary supplementary item’s offset from the section or layout it’s attached to.

var alignment: NSRectAlignment

The alignment of the boundary supplementary item relative to the section or layout it’s attached to.

var extendsBoundary: Bool

A Boolean value that indicates whether a boundary supplementary item extends the content area of the section or layout it’s attached to.

## Relationships

### Inherits From

- NSCollectionLayoutSupplementaryItem

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSObjectProtocol

## See Also

### Appearance

class NSCollectionLayoutAnchor

An object that defines how to attach a supplementary item to an item in a collection view.

class NSCollectionLayoutSupplementaryItem

An object used to add an extra visual decoration to an item in a collection view.

class NSCollectionLayoutDecorationItem

An object used to add a background to a section of a collection view.

