

- SwiftUI
- NSViewControllerRepresentable
-  makeCoordinator() 

Instance Method

# makeCoordinator()

Creates the custom object that you use to communicate changes from your view controller to other parts of your SwiftUI interface.

macOS 10.15+

``` source
@MainActor @preconcurrency
func makeCoordinator() -> Self.Coordinator
```

**Required** Default implementation provided.

## Discussion

Implement this method if changes to your view controller might affect other parts of your app. In your implementation, create a custom Swift instance that can communicate with other parts of your interface. For example, you might provide an instance that binds its variables to SwiftUI properties, causing the two to remain synchronized. If your view controller doesn’t interact with other parts of your app, providing a coordinator is unnecessary.

SwiftUI calls this method before calling the makeNSViewController(context:) method. The system provides your coordinator instance either directly or as part of a context structure when calling the other methods of your representable instance.

## Default Implementations

### NSViewControllerRepresentable Implementations

func makeCoordinator() -> Self.Coordinator

Creates an object to coordinate with the AppKit view controller.

## See Also

### Providing a custom coordinator object

associatedtype Coordinator = Void

A type to coordinate with the view controller.

**Required**

