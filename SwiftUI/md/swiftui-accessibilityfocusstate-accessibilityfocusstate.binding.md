

- SwiftUI
- AccessibilityFocusState
-  AccessibilityFocusState.Binding 

Structure

# AccessibilityFocusState.Binding

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
@propertyWrapper @frozen
struct Binding
```

## Topics

### Getting the state

var projectedValue: AccessibilityFocusState&lt;Value>.Binding

The currently focused element.

var wrappedValue: Value

The underlying value referenced by the bound property.

## See Also

### Getting the state

var projectedValue: AccessibilityFocusState&lt;Value>.Binding

A projection of the state value that can be used to establish bindings between view content and accessibility focus placement.

var wrappedValue: Value

The current state value, taking into account whatever bindings might be in effect due to the current location of focus.

