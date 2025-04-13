

- UIKit
-  UITextSelectionDisplayInteractionDelegate 

Protocol

# UITextSelectionDisplayInteractionDelegate

An object you use to customize the presentation of text selections in your interface.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+tvOS 17.0+visionOS 1.0+

``` source
@MainActor
protocol UITextSelectionDisplayInteractionDelegate : NSObjectProtocol
```

## Overview

Adopt the UITextSelectionDisplayInteractionDelegate protocol in a custom type that you use to customize the selection UI implementation. The UITextSelectionDisplayInteraction object manages separate views to draw the text selection, the handles for the selected text range, and the insertion-point caret. Use this protocol if you use a custom view to manage these views instead of the text input view. For example, provide a container view if you draw the selection UI behind your text view’s content.

## Topics

### Providing a container view

func selectionContainerViewBelowText(for: UITextSelectionDisplayInteraction) -> UIView?

Returns the container view to hold the selection-related highlight and detail views.

## Relationships

### Inherits From

- NSObjectProtocol

## See Also

### Managing the drawing view

var delegate: (any UITextSelectionDisplayInteractionDelegate)?

A delegate that provides a container view to manage the system-supplied selection views.

