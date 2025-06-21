Framework

# Observation

Make responsive apps that update the presentation when underlying data changes.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

## [Overview](/documentation/Observation#Overview)

Observation provides a robust, type-safe, and performant implementation of the observer design pattern in Swift. This pattern allows an observable object to maintain a list of observers and notify them of specific or general state changes. This has the advantages of not directly coupling objects together and allowing implicit distribution of updates across potential multiple observers.

The Observation frameworks provides the following capabilities:

*   Marking a type as observable
    
*   Tracking changes within an instance of an observable type
    
*   Observing and utilizing those changes elsewhere, such as in an app’s user interface
    

To declare a type as observable, attach the [`Observable()`](/documentation/observation/observable\(\)) macro to the type declaration. This macro declares and implements conformance to the [`Observable`](/documentation/observation/observable) protocol to the type at compile time.

```swift

```swift
@Observable
```swift
```swift
class Car {
```
```
    var name: String = ""
    var needsRepairs: Bool = false
    
    init(name: String, needsRepairs: Bool = false) {
        self.name = name
        self.needsRepairs = needsRepairs
    }
}
```

```

To track changes, use the [`withObservationTracking(_:onChange:)`](/documentation/observation/withobservationtracking\(_:onchange:\)) function. For example, in the following code, the function calls the `onChange` closure when a car’s name changes. However, it doesn’t call the closure when a car’s `needsRepair` flag changes. That’s because the function only tracks properties read in its `apply` closure, and the closure doesn’t read the `needsRepair` property.

```swift
```swift
```swift
```swift
```swift
```swift
func render() {
```
```
    withObservationTracking {
        for car in cars {
            print(car.name)
        }
    } onChange: {
        print("Schedule renderer.")
    }
}
```
```
```
```

## [Topics](/documentation/Observation#topics)

### [Observable conformance](/documentation/Observation#Observable-conformance)

[`macro Observable()`](/documentation/observation/observable\(\))

Defines and implements conformance of the Observable protocol.

```swift
```swift
```swift
protocol Observable
```
```

A type that emits notifications to observers when underlying data changes.
```

### [Change tracking](/documentation/Observation#Change-tracking)

```swift
```swift
```swift
```swift
func withObservationTracking<T>(() -> T, onChange: @autoclosure () -> () -> Void) -> T
```
```

Tracks access to properties.
```
```swift
```swift
```swift
struct ObservationRegistrar
```
```

Provides storage for tracking and access to data changes.
```
```

### [Observation in SwiftUI](/documentation/Observation#Observation-in-SwiftUI)

[

Managing model data in your app](/documentation/SwiftUI/Managing-model-data-in-your-app)

Create connections between your app’s data model and views.

[

Migrating from the Observable Object protocol to the Observable macro](/documentation/SwiftUI/Migrating-from-the-observable-object-protocol-to-the-observable-macro)

Update your existing app to leverage the benefits of Observation in Swift.

### [Macros](/documentation/Observation#Macros)

[`macro ObservationIgnored()`](/documentation/observation/observationignored\(\))

Disables observation tracking of a property.

[`macro ObservationTracked()`](/documentation/observation/observationtracked\(\))

Synthesizes a property for accessors.