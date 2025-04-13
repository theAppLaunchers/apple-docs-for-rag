

- SwiftUI
- StateObject
-  init(wrappedValue:) 

Initializer

# init(wrappedValue:)

Creates a new state object with an initial wrapped value.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
nonisolated
init(wrappedValue thunk: @autoclosure @escaping () -> ObjectType)
```

## Parameters 

`thunk`  

An initial value for the state object.

## Discussion

You typically don’t call this initializer directly. Instead, SwiftUI calls it for you when you declare a property with the `@StateObject` attribute in an App, Scene, or View and provide an initial value:

```
struct MyView: View {
    @StateObject private var model = DataModel()

    // ...
}
```

SwiftUI creates only one instance of the state object for each container instance that you declare. In the above code, SwiftUI creates `model` only the first time it initializes a particular instance of `MyView`. On the other hand, each instance of `MyView` creates a distinct instance of the data model. For example, each of the views in the following VStack has its own model storage:

```
var body: some View {
    VStack {
        MyView()
        MyView()
    }
}
```

### Initialize using external data

If the initial state of a state object depends on external data, you can call this initializer directly. However, use caution when doing this, because SwiftUI only initializes the object once during the lifetime of the view — even if you call the state object initializer more than once — which might result in unexpected behavior. For more information and an example, see StateObject.

