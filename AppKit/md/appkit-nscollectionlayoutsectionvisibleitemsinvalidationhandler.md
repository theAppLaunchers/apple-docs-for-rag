

- AppKit
-  NSCollectionLayoutSectionVisibleItemsInvalidationHandler 

Type Alias

# NSCollectionLayoutSectionVisibleItemsInvalidationHandler

A closure called before each layout cycle to allow modification of items in a section immediately before they’re displayed.

macOS

``` source
typealias NSCollectionLayoutSectionVisibleItemsInvalidationHandler = ([any NSCollectionLayoutVisibleItem], NSPoint, any NSCollectionLayoutEnvironment) -> Void
```

## Discussion

Each section of a collection view layout can have a visible items invalidation handler. You use this handler to perform custom animations on the items currently visible within the bounds of that section. The handler is called before each layout cycle, any time an animation occurs in that section due to changes such as adding or removing items, scrolling the section, or rotating the device.

- Swift
- Objective-C

```
let section = NSCollectionLayoutSection(group: group)

section.visibleItemsInvalidationHandler = { visibleItems, scrollOffset, layoutEnvironment in
    // Perform animations on the visible items.
}
```

```
NSCollectionLayoutSection *section = [NSCollectionLayoutSection sectionWithGroup:group];

[section setVisibleItemsInvalidationHandler:^(NSArray> *visibleItems, CGPoint contentOffset, id layoutEnvironment) {
    // Perform animations on the visible items.
}];
```

## See Also

### Layout updates

protocol NSCollectionLayoutVisibleItem

An item that’s currently visible within the bounds of a section.

