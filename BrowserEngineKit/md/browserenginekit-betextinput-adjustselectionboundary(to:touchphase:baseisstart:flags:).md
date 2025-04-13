

- BrowserEngineKit
- BETextInput
-  adjustSelectionBoundary(to:touchPhase:baseIsStart:flags:) 

Instance Method

# adjustSelectionBoundary(to:touchPhase:baseIsStart:flags:)

Adjusts the selection’s start or end boundary specified by `boundaryIsStart` to the `point`

iOS 17.4+iPadOS 17.4+tvOS 17.4+visionOS 1.1+

``` source
func adjustSelectionBoundary(
    to point: CGPoint,
    touchPhase touch: BESelectionTouchPhase,
    baseIsStart boundaryIsStart: Bool,
    flags: BESelectionFlags
)
```

**Required**

## Parameters 

`point`  

The new boundary point of the selection.

`touch`  

The touch phase of the gesture.

`boundaryIsStart`  

`true` if the `point` is at the new start of the selection; `false` if it’s at the end.

`flags`  

Extra information about the selection.

## Mentioned in 

Integrating custom browser text views with UIKit

## Discussion

For example, the selection’s boundary would be adjusted when the user moves the selection handles

Indicate to the system that the change was handled by invoking: -\[BETextInteraction selectionBoundaryAdjustedToPoint:touchPhase:flags:\]

Adjusts the start or end boundary of the current selection to the given point.

## Overview

When you receive this method, call selectionBoundaryAdjusted(to:touchPhase:flags:) to notify the system that your text view handled the update.

## See Also

### Handling text gestures

func updateCurrentSelection(to: CGPoint, from: BEGestureType, in: UIGestureRecognizer.State)

Indicates the `point` the text interaction gesture is tracking has changed

**Required**

func setSelection(from: CGPoint, to: CGPoint, gesture: BEGestureType, state: UIGestureRecognizer.State)

Notifies the text view that its selection needs to change to the text between the given points.

**Required**

func textInteractionGesture(BEGestureType, shouldBeginAt: CGPoint) -> Bool

Returns whether a gesture with the given `gestureType` should begin for the given `point`

**Required**

