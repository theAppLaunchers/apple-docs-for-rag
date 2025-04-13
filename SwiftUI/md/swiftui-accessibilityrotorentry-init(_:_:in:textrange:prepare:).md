

- SwiftUI
- AccessibilityRotorEntry
-  init(\_:\_:in:textRange:prepare:) 

Initializer

# init(\_:\_:in:textRange:prepare:)

Create a Rotor entry with a specific label, identifier and namespace, and with an optional range.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
init(
    _ label: L,
    _ id: ID,
    in namespace: Namespace.ID,
    textRange: Range? = nil,
    prepare: @escaping () -> Void = {}
) where L : StringProtocol
```

## Parameters 

`label`  

Localized string used to show this Rotor entry to users.

`id`  

Used to find the UI element associated with this Rotor entry. This identifier and namespace should match a call to `accessibilityRotorEntry(id:in)`.

`namespace`  

Namespace for this identifier. Should match a call to `accessibilityRotorEntry(id:in)`.

`textRange`  

Optional range of text associated with this Rotor entry. This should be a range within text that is set as the accessibility label or accessibility value of the associated element.

`prepare`  

Optional closure to run before a Rotor entry is navigated to, to prepare the UI as needed. This should be used to bring the Accessibility element on-screen, if scrolling is needed to get to it.

## See Also

### Creating an identified rotor entry in a namespace

init(_:id:in:textRange:prepare:)

Create a Rotor entry with a specific label, identifier and namespace, and with an optional range.

