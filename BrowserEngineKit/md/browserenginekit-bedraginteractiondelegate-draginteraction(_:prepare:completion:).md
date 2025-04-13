

- BrowserEngineKit
- BEDragInteractionDelegate
-  dragInteraction(\_:prepare:completion:) 

Instance Method

# dragInteraction(\_:prepare:completion:)

Called when the drag interaction has begun, to allow the delegate to prepare for the drag session before the system requests drag items through `-dragInteraction:itemsForBeginningSession:`.

iOS 17.4+iPadOS 17.4+

``` source
@MainActor
optional func dragInteraction(
    _ dragInteraction: BEDragInteraction,
    prepare session: any UIDragSession,
    completion: @escaping () -> Bool
)
```

## Parameters 

`dragInteraction`  

The drag interaction that called this method.

`session`  

The drag session to prepare for.

`completion`  

A completion handler you call when you finish preparing for the drag session.

## Discussion

You should call the `completion` block as soon as the drag session is prepared, as to minimize the delay from the user interaction from the drag gesture. There is a system-defined timeout before the drag session is failed if the `completion` is not called in time. The `completion` block returns `YES` if the drag session did prepare successfully prepare, and `NO` otherwise, to allow clients to perform any clean-up if necessary.

Tells the delegate to prepare for a drag session.

## Overview

Call the completion handler as soon as you’re prepared to handle the drag session, because any delay might appear as a user-interface glitch to the person using your browser app.

Important

If you don’t call the completion handler within a time interval that the operating system expects, it cancels the drag interaction.

If you successfully prepare for the drag session, pass `true` as the parameter in the completion handler; otherwise, pass `false`.

## See Also

### Participating in drag gestures

func dragInteraction(BEDragInteraction, itemsForAddingTo: any UIDragSession, forTouchAt: CGPoint, completion: ([UIDragItem]) -> Bool)

The asynchronous counterpart to `-dragInteraction:itemsForAddingToSession:withTouchAtPoint:` to allow touches on this view to add items to an existing drag session. Please refer to the aforementioned delegate method for its full documentation.

