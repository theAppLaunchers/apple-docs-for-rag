

- UIKit
- UICollectionViewLayout
-  invalidationContext(forBoundsChange:) 

Instance Method

# invalidationContext(forBoundsChange:)

Retrieves a context object that defines the portions of the layout that should change when a bounds change occurs.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func invalidationContext(forBoundsChange newBounds: CGRect) -> UICollectionViewLayoutInvalidationContext
```

## Parameters 

`newBounds`  

The new bounds for the collection view.

## Return Value

An invalidation context that describes the changes that need to be made. Do not return nil.

## Discussion

The default implementation of this method creates an instance of the class provided by the invalidationContextClass class method and returns it. If you want to use a custom invalidation context object with your layout, always override that method and return your custom class.

You can override this method if you want to create and configure your custom invalidation context in response to a bounds change. If you override this method, you must call `super` first to get the invalidation context object to return. After getting this object, set any custom properties and return it.

## See Also

### Invalidating the layout

func invalidateLayout()

Invalidates the current layout and triggers a layout update.

func invalidateLayout(with: UICollectionViewLayoutInvalidationContext)

Invalidates the current layout using the information in the provided context object.

class var invalidationContextClass: AnyClass

Returns the class to use when creating an invalidation context for the layout.

func shouldInvalidateLayout(forBoundsChange: CGRect) -> Bool

Asks the layout object if the new bounds require a layout update.

func shouldInvalidateLayout(forPreferredLayoutAttributes: UICollectionViewLayoutAttributes, withOriginalAttributes: UICollectionViewLayoutAttributes) -> Bool

Asks the layout object if changes to a self-sizing cell require a layout update.

func invalidationContext(forPreferredLayoutAttributes: UICollectionViewLayoutAttributes, withOriginalAttributes: UICollectionViewLayoutAttributes) -> UICollectionViewLayoutInvalidationContext

Retrieves a context object that identifies the portions of the layout that should change in response to dynamic cell changes.

func invalidationContext(forInteractivelyMovingItems: [IndexPath], withTargetPosition: CGPoint, previousIndexPaths: [IndexPath], previousPosition: CGPoint) -> UICollectionViewLayoutInvalidationContext

Retrieves a context object that identifies the items that are being interactively moved in the layout.

func invalidationContextForEndingInteractiveMovementOfItems(toFinalIndexPaths: [IndexPath], previousIndexPaths: [IndexPath], movementCancelled: Bool) -> UICollectionViewLayoutInvalidationContext

Retrieves a context object that identifies the items that were moved

