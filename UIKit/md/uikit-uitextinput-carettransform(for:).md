

- UIKit
- UITextInput
-  caretTransform(for:) 

Instance Method

# caretTransform(for:)

Returns the transform to apply to the caret prior to drawing.

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+tvOS 17.4+visionOS 1.1+

``` source
@MainActor
optional func caretTransform(for position: UITextPosition) -> CGAffineTransform
```

## Parameters 

`position`  

An object that identifies the insertion point in a text input area.

## Return Value

The transform to apply to the caret during drawing.

## Discussion

Use this method to provide the text system with the same transform you apply to the text in your view. Providing this transform lets the system render the caret accurately relative to the text. For example, if the text is rotated, return a transform with the same rotation factor to ensure the caret appears in the correct position and orientation relative to the text. If you don’t implement this method, the system applies the identity transform to the caret.

## See Also

### Providing the caret layout information

func caretRect(for: UITextPosition) -> CGRect

Returns a rectangle to draw the caret at a specified insertion point.

**Required**

