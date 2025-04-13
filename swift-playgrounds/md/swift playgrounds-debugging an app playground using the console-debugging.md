

- Swift Playgrounds
-  Debugging an App Playground using the Console 

Article

# Debugging an App Playground using the Console

Learn different methods to debug your code using console output.

## Overview

When writing code in Swift Playgrounds, you can debug your playgrounds by using print statements and viewing their output in the console. You can filter statements in the console to find specific outputs.

## Add a print statement

Call `print(_:separator:terminator)` in the code you’d like to debug and add any items you’d like to output to the console. These items output as `String` values, the same as the output obtained by calling `String(item)`. To customize your debug output for any type, you can add CustomDebugStringConvertible conformance to provide your own implementation for `debugDescription`. This allows you to print custom `String` representations for any type and view them in the console.

If you’re trying to debug a SwiftUI view, you need to adjust your approach. Because SwiftUI is a declarative framework, you can’t add an imperative `print` call inside your view declaration. This is because the view `body` property expects to return a View value. To resolve this, you can use one of several approaches.

One approaach to debug your declarative code is to attach the `onAppear(perform:)` modifier to a view in your `body`, and call `print` when the view first appears:

```
Image(systemName: "globe")
    .onAppear {
        print("This is the debug output.")
    }
```

You could also add an extension on `View` that returns itself and calls the `print` method:

```
extension View {
    func printOutput(_ value: Any) -> Self {
        print(value)
        return self
    }
}
```

You can then use `printOutput` as a view modifier to print debug information to the console when the view is built:

```
VStack {
   ForEach(colors, id: \.self) { color in
      Circle()
         .foregroundColor(color)
         .printOutput(color)
   }
}
```

## Understand when and why your views change

Another approach that’s particularly useful when debugging SwiftUI view updates is to call the internal method `Self._printChanges()` from the `body` of the view — instead of calling `print`. This records which property caused the view to update and sends that information to the console. In addition to providing property names, `@self` marks the change to the view value, and `@identity` marks the change to the view’s identity.

```
var body: some View {
    let _ = Self._printChanges()
    // View code 
}
```

## See your app’s output in the Console

Press the console button in the code editor to show and hide the console. To adjust the size of the console, you can drag to increase or decrease the available space.

To filter results, tap the filter button and enter a phrase you’d like to filter on. The remaining results filter based upon this input.

You can tap to select a result, which allows you to select it as text or to clear the console output by deleting the text.

## See Also

### App playgrounds

Adding a Swift package to your app playground

Extend the functionality of your app playground by finding and adding a publicly available Swift package.

Previewing SwiftUI views in Swift Playgrounds

Use the canvas in Swift Playgrounds to see a live preview of the SwiftUI views in your app.

Requesting access to capabilities for your app playground

Request access for your app to protected resources, services, or device hardware such as sensors.

Importing sample content into user app playgrounds

Learn how to bring sample code into your app playground.

