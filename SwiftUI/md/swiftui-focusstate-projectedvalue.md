

- SwiftUI
- FocusState
-  projectedValue 

Instance Property

# projectedValue

A projection of the focus state value that returns a binding.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var projectedValue: FocusState.Binding { get }
```

## Discussion

When focus is outside any view that is bound to this state, the wrapped value is `nil` for optional-typed state or `false` for Boolean state.

In the following example of a simple navigation sidebar, when the user presses the Filter Sidebar Contents button, focus moves to the sidebar’s filter text field. Conversely, if the user moves focus to the sidebar’s filter manually, then the value of `isFiltering` automatically becomes `true`, and the sidebar view updates.

```
struct Sidebar: View {
    @State private var filterText = ""
    @FocusState private var isFiltering: Bool

    var body: some View {
        VStack {
            Button("Filter Sidebar Contents") {
                isFiltering = true
            }

            TextField("Filter", text: $filterText)
                .focused($isFiltering)
        }
    }
}
```

## See Also

### Inspecting the focus state

struct Binding

A property wrapper type that can read and write a value that indicates the current focus location.

var wrappedValue: Value

The current state value, taking into account whatever bindings might be in effect due to the current location of focus.

