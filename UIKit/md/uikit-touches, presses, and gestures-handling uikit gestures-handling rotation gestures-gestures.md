

- UIKit
- Touches, presses, and gestures
- Handling UIKit gestures
-  Handling rotation gestures 

Article

# Handling rotation gestures

Measure the relative rotation of two fingers on the screen, and use that motion to rotate your content.

## Overview

A rotation gesture is a continuous gesture that occurs when the first two fingers that touch the screen rotate around each other. Use the UIRotationGestureRecognizer class to detect rotation gestures.

You can attach a gesture recognizer in one of these ways:

- Programmatically. Call the addGestureRecognizer(_:) method of your view.

- In Interface Builder. Drag the appropriate object from the library and drop it onto your view.

Use a rotation gesture recognizer when you want to use rotational movements as input to your app. Rotational gestures are commonly used to manipulate objects onscreen. For example, you might use them to rotate a view or update the value of a custom control. Rotation gestures are continuous, so your action method is called whenever the rotation value changes, giving you a chance to update your content.

The gesture recognizer reports rotation values in radians. If you imagine a line between a person’s fingers, the line created by the fingers at their initial positions represents the initial point for measurements, and therefore represents a rotation angle of `0`. As a person’s fingers move, a new line is created between the fingers at each new location. The gesture recognizer measures the angle between the initial line and each new line and places the resulting value in its rotation property.

A rotation gesture recognizer enters the UIGestureRecognizer.State.began state as soon as the position of a person’s fingers changes in a way that indicates that rotation has begun. After that initial change, subsequent changes cause the gesture recognizer to enter the UIGestureRecognizer.State.changed state and update the angle of rotation. When a person’s fingers lift from the screen, the gesture recognizer enters the UIGestureRecognizer.State.ended state.

Important

Take care when applying rotation values to your content, or you might get unexpected results. The rotation reported by the gesture recognizer represents the angle between the current finger position and the initial finger position. If you apply each new rotation value as is to your content, each new value compounds the previous one, causing your content to rotate too fast. Instead, cache the original value of your content, apply the rotation to the original value, and apply the new value back to your content. Alternatively, reset the rotation factor to `0.0` after applying each new change,

The following code demonstrates how to rotate a view in a way that follows a person’s fingers. This action method applies the current rotation factor to the view’s transform and then resets the gesture recognizer’s rotation property to `0.0`. Resetting the rotation factor causes the gesture recognizer to report only the amount of change since the value was reset, which results in the linear rotation of the view

```
@IBAction func rotatePiece(_ gestureRecognizer : UIRotationGestureRecognizer) {   // Move the anchor point of the view's layer to the center of a 
   // person's two fingers. This creates a more natural looking rotation. 
   guard gestureRecognizer.view != nil else { return }

   if gestureRecognizer.state == .began || gestureRecognizer.state == .changed {
      gestureRecognizer.view?.transform = gestureRecognizer.view!.transform.rotated(by: gestureRecognizer.rotation)
      gestureRecognizer.rotation = 0
   }}

```

If the code for your rotation gesture recognizer isn’t called, or isn’t working correctly, check to see if the following conditions are true, and make corrections as needed:

- The isUserInteractionEnabled property of the view is set to true. Image views and labels set this property to false by default.

- At least two fingers are touching the screen.

- You’re applying rotation factors to your content correctly. Over-rotation happens when you apply the same rotation value more than once. To fix this problem, set the rotation property to `0.0` after applying the current rotation value to your content.

## See Also

### Gestures

Handling tap gestures

Use brief taps on the screen to implement button-like interactions with your content.

Handling long-press gestures

Detect extended duration taps on the screen, and use them to reveal contextually relevant content.

Handling pan gestures

Trace the movement of fingers around the screen, and apply that movement to your content.

Handling swipe gestures

Detect a horizontal or vertical swipe motion on the screen, and use it to trigger navigation through your content.

Handling pinch gestures

Track the distance between two fingers and use that information to scale or zoom your content.

