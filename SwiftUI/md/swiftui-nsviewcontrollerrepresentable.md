

- SwiftUI
-  NSViewControllerRepresentable 

Protocol

# NSViewControllerRepresentable

A wrapper that you use to integrate an AppKit view controller into your SwiftUI interface.

macOS 10.15+

``` source
@MainActor @preconcurrency
protocol NSViewControllerRepresentable : View where Self.Body == Never
```

## Overview

Use an NSViewControllerRepresentable instance to create and manage an NSViewController object in your SwiftUI interface. Adopt this protocol in one of your app’s custom instances, and use its methods to create, update, and tear down your view controller. The creation and update processes parallel the behavior of SwiftUI views, and you use them to configure your view controller with your app’s current state information. Use the teardown process to remove your view controller cleanly from your SwiftUI. For example, you might use the teardown process to notify other objects that the view controller is disappearing.

To add your view controller into your SwiftUI interface, create your `NSViewControllerRepresentable` instance and add it to your SwiftUI interface. The system calls the methods of your custom instance at appropriate times.

The system doesn’t automatically communicate changes occurring within your view controller to other parts of your SwiftUI interface. When you want your view controller to coordinate with other SwiftUI views, you must provide a Coordinator instance to facilitate those interactions. For example, you use a coordinator to forward target-action and delegate messages from your view controller to any SwiftUI views.

Warning

SwiftUI fully controls the layout of the AppKit view controller’s view using the view’s frame and bounds properties. Don’t directly set these layout-related properties on the view managed by an `NSViewControllerRepresentable` instance from your own code because that conflicts with SwiftUI and results in undefined behavior.

## Topics

### Creating and updating the view controller

func makeNSViewController(context: Self.Context) -> Self.NSViewControllerType

Creates the view controller object and configures its initial state.

**Required**

func updateNSViewController(Self.NSViewControllerType, context: Self.Context)

Updates the state of the specified view controller with new information from SwiftUI.

**Required**

typealias Context

associatedtype NSViewControllerType : NSViewController

The type of view controller to present.

**Required**

### Specifying a size

func sizeThatFits(ProposedViewSize, nsViewController: Self.NSViewControllerType, context: Self.Context) -> CGSize?

Given a proposed size, returns the preferred size of the composite view.

**Required** Default implementation provided.

### Cleaning up the view controller

static func dismantleNSViewController(Self.NSViewControllerType, coordinator: Self.Coordinator)

Cleans up the presented view controller (and coordinator) in anticipation of its removal.

**Required** Default implementation provided.

### Providing a custom coordinator object

func makeCoordinator() -> Self.Coordinator

Creates the custom object that you use to communicate changes from your view controller to other parts of your SwiftUI interface.

**Required** Default implementation provided.

associatedtype Coordinator = Void

A type to coordinate with the view controller.

**Required**

### Performing layout

typealias LayoutOptions

## Relationships

### Inherits From

- View

## See Also

### Adding AppKit views to SwiftUI view hierarchies

protocol NSViewRepresentable

A wrapper that you use to integrate an AppKit view into your SwiftUI view hierarchy.

struct NSViewRepresentableContext

Contextual information about the state of the system that you use to create and update your AppKit view.

struct NSViewControllerRepresentableContext

Contextual information about the state of the system that you use to create and update your AppKit view controller.

