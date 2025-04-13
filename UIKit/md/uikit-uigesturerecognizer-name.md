

- UIKit
- UIGestureRecognizer
-  name 

Instance Property

# name

The unique name of the gesture recognizer.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+tvOS 11.0+visionOS 1.0+

``` source
@MainActor
var name: String? { get set }
```

## Discussion

Assign a string to this property that uniquely identifies the gesture recognizer. Use this name to distinguish one gesture recognizer from another during debugging, or to specify a relationship between gestures in SwiftUI and UIKit.

For example, you can assign a SwiftUI gesture a name when you create it using gesture(_:name:isEnabled:), as the following code shows:

```
// SwiftUI code
struct TapGestureView: View {
    @State private var tapLocation: CGPoint = .zero

    var tap: some Gesture {
        DragGesture(minimumDistance: 0, coordinateSpace: .local)
            .onEnded { event in
                tapLocation = event.location
            }
    }

    var body: some View {
        Text("Tap location: \(tapLocation.debugDescription)")
            .frame(width: 120, height: 120)
            .background(Color.gray)
            .gesture(tap, name: "MyTap")
    }
}
```

Then, you can use this name property to refer to the gesture from UIKit. For example, you might do this in your implementation of gestureRecognizer(_:shouldRequireFailureOf:), as the following code shows:

```
// UIKit code
class ViewController: UIViewController, UIGestureRecognizerDelegate {  

    func gestureRecognizer(_ gestureRecognizer: UIGestureRecognizer, 
        shouldRequireFailureOf other: UIGestureRecognizer) -> Bool {
        return other.name == "MyTap"
    }

    // ...
}
```

