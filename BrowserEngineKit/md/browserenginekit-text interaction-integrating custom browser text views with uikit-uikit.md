

- BrowserEngineKit
- Text interaction
-  Integrating custom browser text views with UIKit 

Article

# Integrating custom browser text views with UIKit

Process keyboard interactions asynchronously in your iOS browser app’s text view.

## Overview

iOS apps that draw custom text views adopt the UITextInput protocol to inform the text input system about changes in state related to text input and selection.

In browser apps, the text input system might need information that your app prepares by communicating with an extension asynchronously, or information that the app prepares by executing Javascript from a web site. In these situations, your text view additionally adopts the BETextInput protocol. The text input system uses this protocol to make asynchronous requests for information about the text in your view, and to supply information about gestures that support text interactions, including selecting text and modifying the selection.

### Create your custom text view

`BETextInput` isn’t a complete replacement for `UITextInput`, so a custom view that participates in the text system needs to conform to both protocols.

```
public class MyTextView: UIView, BETextInput, UITextInput {

}
```

Implement the required UITextInput methods in your view class. At runtime, the text system determines whether your text field implements `BETextInput` counterparts to the `UITextInput` methods; if it does, the text system calls the `BETextInput` methods instead of the `UITextInput` methods.

Your custom view’s textInputView is the view that the system uses for all coordinate transforms when handling text-input gestures. When you create the text input view, add a BETextInteraction to the view’s interactions. The operating system uses the `BETextInteraction` to track the state of text-input gestures.

### Accept a delegate object

Create a property asyncInputDelegate of type BETextInputDelegate on your view. The operating system provides delegates when it needs notifications for text input changes; you don’t conform to `BETextInputDelegate` in your code or implement its methods.

```
public class MyTextView: UIView, BETextInput, UITextInput {
   weak var asyncInputDelegate: BETextInputDelegate? = nil
}
```

### Report whether the text view performs actions

Implement canPerformAction(_:withSender:) in your view, returning `true` when your view can perform the action and `false` otherwise. If you return `false`, the operating system doesn’t call the action method even if your class implements it (so responds(to:) with the action method’s selector returns `true`). Return `false` when your view is in a state where it doesn’t handle the action.

### Accept text input

The system tells your text view which writing direction the person is using to input text with setBaseWritingDirection(_:for:).

Implement the handleKeyEntry(_:completionHandler:) method to accept key events from the text input system, which you interpret to insert characters and perform actions for key combinations that the text system doesn’t interpret. Asynchronously process the key event, and call the completion handler when you’re done, passing `true` in the second parameter if you handled the event, `false` otherwise.

The system calls `handleKeyEntry(_:completionHandler:)` multiple times for one keypress:

- Once when someone initially presses the key and it enters the BEKeyEntry.KeyPressState.down state.

- Zero or more times for repeated entry if the key remains pressed down, in which case isKeyRepeating is `true`.

- Once when someone releases the key and it re-enters the BEKeyEntry.KeyPressState.up state.

If you don’t handle the key event and return `false` from the completion handler, call the delegate’s shouldDeferEventHandlingToSystem(for:context:) method to give the system an opportunity to handle the event.

Important

Your text view needs to call the completion handler for each key event it receives, to indicate to the text system that it’s ready for the next event. The operating system processes key events on a serial queue, so if you don’t call the completion handler you block key input to your app.

Additionally, implement shiftKeyStateChanged(fromState:toState:) to discover when someone presses and releases the shift key and when someone engages and disengages the caps lock.

### Report text content and layout

Tell the text system what text is in a given range in your text view with text(in:).

In your implementation of offset(from:to:), report the difference between two text positions, counting the number of insertion points (locations that the text caret can adopt) between the text positions. A negative value means that the first position is after the second position; zero means they are the same position; and a positive value means that the first position is before the second position.

### Select text and respond to selection changes

When the operating system detects that someone is starting a gesture in your text view, it sends your text view textInteractionGesture(_:shouldBeginAt:), passing the type of gesture it detects and the location of the gesture in your view’s coordinate system.

To permit the gesture to proceed, return `true` from this method; otherwise, return `false`.

If you permit the gesture, then as someone selects text in your text view, the text system sends your text view one of the following methods, depending on the gesture:

moveSelection(atBoundary:in:completionHandler:)  
The gesture moves the text selection caret in the given direction.

selectPosition(at:completionHandler:)  
The gesture locates the text selection caret at the given point.

selectText(in:at:completionHandler:)  
The gesture updates the selection to the text contained at the given granularity and point.

updateSelection(extent:boundary:completionHandler:)  
The gesture adjusts the selection to include the text at the given point.

updateCurrentSelection(to:from:in:)  
The operating system changed the point at which it’s tracking the gesture.

setSelection(from:to:gesture:state:)  
The gesture changes the selection to the text between the given points.

adjustSelectionBoundary(to:touchPhase:baseIsStart:flags:)  
The gesture adjusts the selection’s start or end boundary to the text at the given point.

The view’s selectedText property needs to contain the selection and the selectedTextRange property needs to contain the range of the selection. If the selection caret is in the document, then `selectedTextRange` has zero length. If someone hasn’t selected any text, both of these properties need to be `nil`. If the selection is at the beginning of the text document, then return `true` as the value for isSelectionAtDocumentStart; otherwise, return `false`.

As someone continues their text-selection gesture, you need to update the geometry of the selection so that the text system draws the selection UI correctly. Implement selectionRects(for:) and caretRect(for:) to provide the selection geometry to the text system.

Implement updateSelection(extent:boundary:completionHandler:) to get notified when someone modifies the selection.

Note

Your text view also needs to support marked text. *Marked text* is very similar to selected text, and represents a range of text proposed for insertion that someone hasn’t yet confirmed they want. Use distinct display styles for marked and selected text.

### Edit text and support autocorrect

The text system calls delete(in:to:) when someone deletes text using the backspace or delete keys. The direction indicates whether to delete text ahead of or behind the insertion point.

You support autocorrect in your text view by implementing replaceSelectedText(_:withText:), replacing the original text in your text storage with the `replacementText` string.

When the text system requires extra context around the current selection to make autocorrect suggestions, it calls requestTextContextForAutocorrection(completionHandler:). In the completion handler, return a BETextDocumentContext that includes the complete sentence that contains the selection. If the selection is at a sentence boundary, also include the preceding sentence.

Additionally, implement insert(_:) to accept suggested text from the text system as a BETextSuggestion, for example, when someone uses AutoFill to complete the value for a text field.

### Scroll the text view automatically

Some text interactions — including placing the text cursor in a view and updating the selection range — require a text view to scroll automatically so the person can see the text with which they’re interacting. When the text system needs to automatically scroll your text view, it sends autoscroll(to:), with a point in the coordinate space of your text view’s textInputView that needs to become visible. When the person completes the interaction, the text system sends cancelAutoscroll().

### Provide text alternatives

When someone uses Apple Pencil to enter handwritten text into a text view, text alternatives provide alternate interpretations of the person’s input that the person can choose to replace the transcribed text. To support text alternatives in your browser text view, implement these methods:

add(_:)  
Add text alternatives to the text view for the currently selected text.

insert(_:)  
Insert the given text or one of its alternatives.

removeTextAlternatives()  
Remove the text alternatives for the currently selected text.

alternativesForSelectedText()  
Supply the available text alternatives.

### Respond to someone dismissing the keyboard

On iPad, a person can dismiss the on-screen keyboard from a control on the keyboard UI, which ends the current text-editing session. Implement keyboardWillDismiss() to react to the person dismissing the keyboard while your text view is active. If the browser view that hosts your text control needs to retain first-responder status after someone dismisses the keyboard, for example, to provide keyboard-driven scrolling, or it needs to execute Javascript when someone finishes editing text, use this method to remove keyboard focus from the text control without resigning first-responder status.

## See Also

### Custom text views

Supporting extended text interactions

Share content, add replacement shortcuts, and perform other rich actions in browser text views.

protocol BETextInput

A protocol to which text views conform to asynchronously integrate with the text system.

protocol BETextInputDelegate

A delegate protocol that a browser text view uses to notify the text system of changes.

