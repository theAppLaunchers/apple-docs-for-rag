

- Accessibility
- AccessibilitySettings
-  prefersNonBlinkingTextInsertionIndicator 

Type Property

# prefersNonBlinkingTextInsertionIndicator

A Boolean value that indicates whether the system setting to prefer a nonblinking cursor in editable text fields is on.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
static var prefersNonBlinkingTextInsertionIndicator: Bool { get }
```

## Discussion

The value of this property is true if the system setting for Prefer Non-Blinking Cursor is on; otherwise, false. This preference is relevant for apps that draw custom insertion indicators.

## See Also

### Reducing animation for text insertion indicators

static let prefersNonBlinkingTextInsertionIndicatorDidChangeNotification: NSNotification.Name

A notification that posts when the system setting to prefer a nonblinking cursor in editable text fields changes.

