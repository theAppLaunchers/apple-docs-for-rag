

- Objective-C Runtime
- NSObject
-  initialize() 

Type Method

# initialize()

Initializes the class before it receives its first message.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 1.0+

``` source
class func initialize()
```

## Discussion

The runtime sends initialize() to each class in a program just before the class, or any class that inherits from it, is sent its first message from within the program. Superclasses receive this message before their subclasses.

The runtime sends the initialize() message to classes in a thread-safe manner. That is, initialize() is run by the first thread to send a message to a class, and any other thread that tries to send a message to that class will block until initialize() completes.

The superclass implementation may be called multiple times if subclasses do not implement initialize()—the runtime will call the inherited implementation—or if subclasses explicitly call `[super initialize]`. If you want to protect yourself from being run multiple times, you can structure your implementation along these lines:

```
+ (void)initialize {
  if (self == [ClassName self]) {
    // ... do the initialization ...
  }
}
```

Because initialize() is called in a blocking manner, it’s important to limit method implementations to the minimum amount of work necessary possible. Specifically, any code that takes locks that might be required by other classes in their initialize() methods is liable to lead to deadlocks. Therefore, you should not rely on initialize() for complex initialization, and should instead limit it to straightforward, class local initialization.

### Special Considerations

initialize() is invoked only once per class. If you want to perform independent initialization for the class and for categories of the class, you should implement load() methods.

## See Also

### Related Documentation

init()

Implemented by subclasses to initialize a new object (the receiver) immediately after memory for it has been allocated.

### Initializing a Class

class func load()

Invoked whenever a class or category is added to the Objective-C runtime; implement this method to perform class-specific behavior upon loading.

