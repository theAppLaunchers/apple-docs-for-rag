

- Objective-C Runtime
- NSObject
-  accessibilityNotifiesWhenDestroyed 

Instance Property

# accessibilityNotifiesWhenDestroyed

A Boolean value that indicates whether a custom accessibility object sends a notification when its corresponding UI element is destroyed.

macOS 10.9+

``` source
var accessibilityNotifiesWhenDestroyed: Bool { get }
```

## Discussion

In macOS 10.9 and later, a custom accessibility object that is an NSObject subclass can post accessibility notifications if it meets the following criteria:

- The lifetime of the custom accessibility object must match the lifetime of the corresponding element in the app’s UI.

Typically, a custom accessibility object that acts as a proxy for an onscreen UI element gets autoreleased and deallocated immediately after the app responds to an accessibility request. Such an object can’t post accessibility notifications, because all registered observers get removed as soon as the object is deallocated. To correct this, an app must guarantee that a custom accessibility object remains allocated for as long as its corresponding UI element remains visible.

- The object must post the uiElementDestroyed notification at the appropriate time. The appropriate time is most likely to be when the corresponding UI element is removed from the screen, but it can also be when the object itself is deallocated.

- The object must implement `accessibilityNotifiesWhenDestroyed` and return YES.

