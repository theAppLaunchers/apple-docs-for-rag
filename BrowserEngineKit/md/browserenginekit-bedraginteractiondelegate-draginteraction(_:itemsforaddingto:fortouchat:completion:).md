

- BrowserEngineKit
- BEDragInteractionDelegate
-  dragInteraction(\_:itemsForAddingTo:forTouchAt:completion:) 

Instance Method

# dragInteraction(\_:itemsForAddingTo:forTouchAt:completion:)

The asynchronous counterpart to `-dragInteraction:itemsForAddingToSession:withTouchAtPoint:` to allow touches on this view to add items to an existing drag session. Please refer to the aforementioned delegate method for its full documentation.

iOS 17.4+iPadOS 17.4+

``` source
@MainActor
optional func dragInteraction(
    _ dragInteraction: BEDragInteraction,
    itemsForAddingTo session: any UIDragSession,
    forTouchAt point: CGPoint,
    completion: @escaping ([UIDragItem]) -> Bool
)
```

## Parameters 

`dragInteraction`  

The drag interaction that called this method.

`session`  

An in-progress drag session for adding items to.

`point`  

The location of the person’s touch in the view’s coordinate system.

`completion`  

A completion block you call to add items to the drag session.

## Discussion

If this method is implemented, then the `UIDragInteractionDelegate` counterpart method will no longer be called.

You should call the `completion` block as soon as the items are ready. There is a system-defined timeout before the system will treat the delegate call as returning an empty array. The `completion` block returns `YES` if the drag session did add items to the session successfully, and `NO` otherwise, to allow clients to perform any clean-up if necessary.

Requests items to add to a drag session.

## Overview

This method is the asynchronous counterpart to dragInteraction(_:itemsForAddingTo:withTouchAt:). If your delegate implements this method, then the system calls it and doesn’t call `dragInteraction(_:itemsForAddingTo:withTouchAt:)`.

Call the completion block as soon as items are ready. If you don’t call the block before a system-defined time interval elapses, the system assumes you have no items to add to the session, as if you had called the completion block with an empty array.

The completion block returns `true` if the drag session added the items you supplied, and `false` otherwise.

## See Also

### Participating in drag gestures

func dragInteraction(BEDragInteraction, prepare: any UIDragSession, completion: () -> Bool)

Called when the drag interaction has begun, to allow the delegate to prepare for the drag session before the system requests drag items through `-dragInteraction:itemsForBeginningSession:`.

