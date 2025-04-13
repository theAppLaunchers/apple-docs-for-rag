

- UIKit
- UIControl
-  continueTracking(\_:with:) 

Instance Method

# continueTracking(\_:with:)

Notifies the control when a touch event for the control updates.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func continueTracking(
    _ touch: UITouch,
    with event: UIEvent?
) -> Bool
```

## Parameters 

`touch`  

The touch object containing updated information.

`event`  

The event object containing the touch event.

## Return Value

true if the control should continue tracking touch events or false if it should stop. This value is used to update the isTracking property of the control.

## Discussion

This method is called repeatedly while a touch event is being tracked inside the control’s bounds. The default implementation of this method always returns true. Subclasses can override this method and use it to update their state based on changes to the touch event. If you want to continue tracking the touch event, return true. If you want to stop tracking the touch event, return false.

## See Also

### Tracking touches and redrawing controls

func beginTracking(UITouch, with: UIEvent?) -> Bool

Notifies the control when a touch event enters the control’s bounds.

func endTracking(UITouch?, with: UIEvent?)

Notifies the control when a touch event associated with the control ends.

func cancelTracking(with: UIEvent?)

Notifies the control to cancel tracking related to the specified event.

var isTracking: Bool

A Boolean value that indicates whether the control is currently tracking touch events.

var isTouchInside: Bool

A Boolean value that indicates whether a tracked touch event is currently inside the control’s bounds.

