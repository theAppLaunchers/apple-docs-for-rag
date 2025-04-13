

- AppKit
-  NSCollectionViewCompositionalLayout 

Class

# NSCollectionViewCompositionalLayout

A layout object that lets you combine items in highly adaptive and flexible visual arrangements.

macOS 10.15+

``` source
@MainActor
class NSCollectionViewCompositionalLayout
```

## Overview

A compositional layout is a type of collection view layout. It’s designed to be composable, flexible, and fast, letting you build any kind of visual arrangement for your content by combining—or compositing—each smaller component into a full layout.

A compositional layout is composed of one or more sections that break up the layout into distinct visual groupings. Each section is composed of groups of individual items, the smallest unit of data you want to present. A group might lay out its items in a horizontal row, a vertical column, or a custom arrangement.

You combine the components by building up from items into a group, from groups into a section, and finally into a full layout, like in this example of a basic list layout:

```
func createBasicListLayout() -> NSCollectionViewLayout {
    let itemSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                         heightDimension: .fractionalHeight(1.0))
    let item = NSCollectionLayoutItem(layoutSize: itemSize)

    let groupSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                          heightDimension: .absolute(44))
    let group = NSCollectionLayoutGroup.horizontal(layoutSize: groupSize,
                                                     subitems: [item])

    let section = NSCollectionLayoutSection(group: group)

    let layout = NSCollectionViewCompositionalLayout(section: section)
    return layout
}
```

## Topics

### Creating a Layout

init(section: NSCollectionLayoutSection)

Creates a compositional layout object with a single section.

init(section: NSCollectionLayoutSection, configuration: NSCollectionViewCompositionalLayoutConfiguration)

Creates a compositional layout object with a single section and an additional configuration.

init(sectionProvider: NSCollectionViewCompositionalLayoutSectionProvider)

Creates a compositional layout object with a section provider to supply the layout’s sections.

init(sectionProvider: NSCollectionViewCompositionalLayoutSectionProvider, configuration: NSCollectionViewCompositionalLayoutConfiguration)

Creates a compositional layout object with a section provider and an additional configuration.

### Configuring the Layout

var configuration: NSCollectionViewCompositionalLayoutConfiguration

The layout’s configuration, such as its scroll direction and section spacing.

## Relationships

### Inherits From

- NSCollectionViewLayout

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol

## See Also

### Layouts

Implementing modern collection views

Bring compositional layouts to your app and simplify updating your user interface with diffable data sources.

class NSCollectionViewFlowLayout

A layout that organizes items into a flexible and configurable arrangement.

protocol NSCollectionViewDelegateFlowLayout

A set of methods that a delegate implements to provide layout information to a flow layout object in a collection view.

class NSCollectionViewGridLayout

A layout that displays a single section of items in a row and column grid.

class NSCollectionViewTransitionLayout

An object that implements custom behaviors when changing from one layout to another in a collection view.

class NSCollectionViewLayoutAttributes

An object that contains layout-related attributes for an element in a collection view.

class NSCollectionViewLayout

An abstract base class that you subclass and use to generate layout information for a collection view.

class NSCollectionViewCompositionalLayoutConfiguration

An object that defines scroll direction, section spacing, and headers or footers for the layout.

typealias NSCollectionViewCompositionalLayoutSectionProvider

A closure that creates and returns each of the layout’s sections.

enum NSCollectionLayoutSectionOrthogonalScrollingBehavior

The scrolling behavior of the layout’s sections in relation to the main layout axis.

