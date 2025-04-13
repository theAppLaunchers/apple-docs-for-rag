

- UIKit
- Touches, presses, and gestures
- Handling UIKit gestures
-  Handling pinch gestures 

Article

# Handling pinch gestures

Track the distance between two fingers and use that information to scale or zoom your content.

## Overview

A pinch gesture is a continuous gesture that tracks the distance between the first two fingers that touch the screen. Use the UIPinchGestureRecognizer class to detect pinch gestures.

You can attach a gesture recognizer in one of these ways:

- Programmatically. Call the addGestureRecognizer(_:) method of your view.

- In Interface Builder. Drag the appropriate object from the library and drop it onto your view.

A pinch gesture recognizer reports changes to the distance between two fingers touching the screen. Pinch gestures are continuous, so your action method is called each time the distance between the fingers changes. The distance between the fingers is reported as a scale factor. At the beginning of the gesture, the scale factor is `1.0`. As the distance between the two fingers increases, the scale factor increases proportionally. Similarly, the scale factor decreases as the distance between the fingers decreases. Pinch gestures are used most commonly to change the size of objects or content onscreen. For example, map views use pinch gestures to change the zoom level of the map.

A pinch gesture recognizer enters the UIGestureRecognizer.State.began state only after the distance between the two fingers changes for the first time. After that initial change, subsequent changes to the distance put the gesture recognizer into the UIGestureRecognizer.State.changed state and update the scale factor. When a person’s fingers lift from the screen, the gesture recognizer enters the UIGestureRecognizer.State.ended state.

Important

Take care when applying a pinch gesture recognizer’s scale factor to your content, or you might get unexpected results. Because your action method may be called many times, you can’t simply apply the current scale factor to your content. If you multiply each new scale value by the current value of your content, which has already been scaled by previous calls to your action method, your content will grow or shrink exponentially. Instead, cache the original value of your content, apply the scale factor to that original value, and apply the new value back to your content. Alternatively, reset the scale factor to `1.0` after applying each new change.

The following code demonstrates how to resize a view linearly using a pinch gesture recognizer. This action method applies the current scale factor to the view’s transform and then resets the gesture recognizer’s scale property to `1.0`. Resetting the scale factor causes the gesture recognizer to report only the amount of change since the value was reset, which results in linear scaling of the view.

```
@IBAction func scalePiece(_ gestureRecognizer : UIPinchGestureRecognizer) {   guard gestureRecognizer.view != nil else { return }

   if gestureRecognizer.state == .began || gestureRecognizer.state == .changed {
      gestureRecognizer.view?.transform = (gestureRecognizer.view?.transform.
                    scaledBy(x: gestureRecognizer.scale, y: gestureRecognizer.scale))!
      gestureRecognizer.scale = 1.0
   }}

```

If the code for your pinch gesture recognizer isn’t called, or isn’t working correctly, check to see if the following conditions are true, and make corrections as needed:

- The isUserInteractionEnabled property of the view is set to true. Image views and labels set this property to false by default.

- At least two fingers are touching the screen.

- You’re applying scale factors to your content correctly. Exponential growth of a value happens when you simply apply the scale factor to the current value.

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

Handling rotation gestures

Measure the relative rotation of two fingers on the screen, and use that motion to rotate your content.

