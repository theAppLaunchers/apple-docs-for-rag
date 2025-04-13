

- UIKit
- UICollectionView
-  reorderingCadence 

Instance Property

# reorderingCadence

The speed at which items in the collection view are reordered to show potential drop locations.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
var reorderingCadence: UICollectionView.ReorderingCadence { get set }
```

## Discussion

The default value in this property is UICollectionView.ReorderingCadence.immediate. You might specify a slower cadence when you want to prevent the reordering of items from being a distraction to the user. For example, you might slow it down if immediate reordering makes it more difficult to drop items at the correct location.

## See Also

### Managing drop interactions

var dropDelegate: (any UICollectionViewDropDelegate)?

The delegate object that manages the dropping of items into the collection view.

protocol UICollectionViewDropDelegate

The interface for handling drops in a collection view.

var hasActiveDrop: Bool

A Boolean value that indicates whether the collection view is currently tracking a drop session.

enum ReorderingCadence

Constants indicating the speed at which collection view items are reorganized during a drop.

