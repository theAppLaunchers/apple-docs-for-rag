

- UIKit
- UICollectionView
-  cancelInteractiveTransition() 

Instance Method

# cancelInteractiveTransition()

Tells the collection view to cancel an interactive transition and return to its original layout object.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func cancelInteractiveTransition()
```

## Discussion

Call this method after a call to the startInteractiveTransition(to:completion:) method and after you determine through a gesture recognizer or other event-handling code that the user wants to revert to the collection view’s original layout. This method removes the intermediate transition layout object from the collection view and reinstalls the original layout object. It then performs any final animations to get the collection view’s items from their current positions to the positions specified by the original layout object.

After calling this method, you can also remove the gesture recognizer or event-handling code you installed to manage the interactive portions of the transition.

## See Also

### Changing the layout

var collectionViewLayout: UICollectionViewLayout

The layout used to organize the collected view’s items.

func setCollectionViewLayout(UICollectionViewLayout, animated: Bool)

Changes the collection view’s layout and optionally animates the change.

func setCollectionViewLayout(UICollectionViewLayout, animated: Bool, completion: ((Bool) -> Void)?)

Changes the collection view’s layout and notifies you when the animations complete.

func startInteractiveTransition(to: UICollectionViewLayout, completion: UICollectionView.LayoutInteractiveTransitionCompletion?) -> UICollectionViewTransitionLayout

Changes the collection view’s current layout using an interactive transition effect.

func finishInteractiveTransition()

Tells the collection view to finish an interactive transition by installing the intended target layout.

typealias LayoutInteractiveTransitionCompletion

The completion block called at the end of an interactive transition for a collection view.

