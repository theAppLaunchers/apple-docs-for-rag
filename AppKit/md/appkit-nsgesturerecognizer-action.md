

- AppKit
- NSGestureRecognizer
-  action 

Instance Property

# action

The action method to call when the gesture is recognized.

macOS 10.10+

``` source
@MainActor
var action: Selector? { get set }
```

## Discussion

You specify this method when initializing your gesture recognizer but can also change the method later. The gesture recognizer executes your action method during specific states of the gesture recognition process. Use your action method to perform any app-specific tasks. For example, you might use that method to animate changes onscreen while the gesture is in progress.

The signature of this method must be one of the following:

- Swift
- Objective-C

```
func handleGesture() { }
func handleGesture(gestureRecognizer: NSGestureRecognizer) { }
```

```
- (void)handleGesture;
- (void)handleGesture:(NSGestureRecognizer *)gestureRecognizer;
```

For continuous gestures, it is recommended that you use an action method that accepts the gesture recognizer as a parameter. In your method, use the provided gesture recognizer object to get the current state of the gesture and perform appropriate tasks based on that state.

## See Also

### Accessing the Target and Action

var target: AnyObject?

The object that implements the action method.

