

- BrowserEngineKit
- BETextInteraction
-  delegate 

Instance Property

# delegate

A delegate object that the interaction notifies when the system changes the text selection.

iOS 17.4+iPadOS 17.4+tvOS 17.4+visionOS 1.1+

``` source
@MainActor
weak var delegate: (any BETextInteractionDelegate)? { get set }
```

## See Also

### Text selection

protocol BETextInteractionDelegate

A set of methods that informs you about selection changes in text views.

var textSelectionDisplayInteraction: UITextSelectionDisplayInteraction

An interaction that manages the system’s text-selection UI.

func selectionBoundaryAdjusted(to: CGPoint, touchPhase: BESelectionTouchPhase, flags: BESelectionFlags)

Notifies the system after the text view adjusts its selection.

func selectionChangedWithGesture(at: CGPoint, gesture: BEGestureType, state: UIGestureRecognizer.State, flags: BESelectionFlags)

Notifies the system that the text view changed its selection.

