

- Swift
- Cocoa Design Patterns
-  Managing a Shared Resource Using a Singleton 

Article

# Managing a Shared Resource Using a Singleton

Provide access to a shared resource using a single, shared class instance.

## Overview

You use singletons to provide a globally accessible, shared instance of a class. You can create your own singletons as a way to provide a unified access point to a resource or service that’s shared across an app, like an audio channel to play sound effects or a network manager to make HTTP requests.

### Create a Singleton

You create simple singletons using a static type property, which is guaranteed to be lazily initialized only once, even when accessed across multiple threads simultaneously:

```
class Singleton {
    static let shared = Singleton()
}
```

If you need to perform additional setup beyond initialization, you can assign the result of the invocation of a closure to the global constant:

```
class Singleton {
    static let shared: Singleton = {
        let instance = Singleton()
        // setup code
        return instance
    }()
}
```

## See Also

### Common Patterns

Using Key-Value Observing in Swift

Notify objects about changes to the properties of other objects.

Using Delegates to Customize Object Behavior

Respond to events on behalf of a delegator.

About Imported Cocoa Error Parameters

Learn how Cocoa error parameters are converted to Swift throwing methods.

Handling Cocoa Errors in Swift

Throw and catch errors that use Cocoa’s error types.

