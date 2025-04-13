

- SwiftUI
- StateObject
-  projectedValue 

Instance Property

# projectedValue

A projection of the state object that creates bindings to its properties.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
@MainActor @preconcurrency
var projectedValue: ObservedObject.Wrapper { get }
```

## Discussion

Use the projected value to get a Binding to a property of a state object. To access the projected value, prefix the property name with a dollar sign (`$`). For example, you can get a binding to a model’s `isEnabled` Boolean so that a Toggle can control the value:

```
struct MyView: View {
    @StateObject private var model = DataModel()

    var body: some View {
        Toggle("Enabled", isOn: $model.isEnabled)
    }
}
```

Important

A `Binding` created by the projected value must only be read from, or written to by the main actor. Failing to do so may result in undefined behavior, or data loss. When this occurs, SwiftUI will issue a runtime warning. In a future release, a crash will occur instead.

## See Also

### Getting the value

var wrappedValue: ObjectType

The underlying value referenced by the state object.

