

- UIKit
- UIKeyCommand
-  allowsAutomaticMirroring 

Instance Property

# allowsAutomaticMirroring

A Boolean value that determines whether the system automatically swaps input strings for some keyboard shortcuts when the interface direction changes.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

``` source
@MainActor
var allowsAutomaticMirroring: Bool { get set }
```

## Discussion

When a key command represents a direction-related action, it’s common to specify an input string that conveys that direction. For example, Safari uses Command-\[ to go back to the previous page, and Command-\] to go forward to the next page. Because directions are different in left-to-right and right-to-left interfaces, this property lets the system swap some input strings to match the current language direction.

When the value of this property is true, iOS 15 and later automatically swaps input strings that contain brackets `[]`, braces `{}`, parenthesis `()`, angle brackets `<>`, or arrow keys when the interface directionality changes. This behavior eliminates the need for you to create different key commands for left-to-right and right-to-left interfaces. Set this property to false if you already change this item’s shortcut to support both left-to-right and right-to-left interfaces. You might also set it to false to keep the same shortcut regardless of the interface’s directionality.

The default value of this property is true. However, if you set the allowsAutomaticLocalization property to false, the system disables this feature regardless of the property’s value.

## See Also

### Localizing keyboard shortcuts

var allowsAutomaticLocalization: Bool

A Boolean value that determines whether the system automatically remaps keyboard shortcuts based on the keyboard layout.

