

- UIKit
- UICollectionViewTransitionLayout
-  currentLayout 

Instance Property

# currentLayout

The collection view’s current layout object.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
var currentLayout: UICollectionViewLayout { get }
```

## Discussion

This object provides the layout attributes representing the initial position of items in the collection view. If you ultimately cancel the transition, the collection view animates its items back to the positions provided by this object.

## See Also

### Accessing the layout objects

var nextLayout: UICollectionViewLayout

The collection view’s new layout object.

