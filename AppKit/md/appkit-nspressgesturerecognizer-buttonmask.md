

- AppKit
- NSPressGestureRecognizer
-  buttonMask 

Instance Property

# buttonMask

A bit mask of the buttons required to recognize this press.

macOS 10.10+

``` source
@MainActor
var buttonMask: Int { get set }
```

## Discussion

Bit 0 represents the primary button, bit 1 is the secondary button, and so on. So to track clicks of the secondary button, assign the value `0x2` (which corresponds to a `1` in bit 1) to this property. The default value of this property is `0x1`, which detects clicks in the primary mouse button.

Changing the value of this property also sets the values of the delaysPrimaryMouseButtonEvents, delaysSecondaryMouseButtonEvents, and delaysOtherMouseButtonEvents properties to true for each of the buttons you specified.

## See Also

### Configuring the Gesture Recognizer

var allowableMovement: CGFloat

The maximum movement of the mouse in the view before the gesture fails.

var minimumPressDuration: TimeInterval

The minimum time (in seconds) that the user must hold the mouse button in the view for a valid gesture.

var numberOfTouchesRequired: Int

The number of necessary touches on a Touch Bar for the gesture recognizer to match.

