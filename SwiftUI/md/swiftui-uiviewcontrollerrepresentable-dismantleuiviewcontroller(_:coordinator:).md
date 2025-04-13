

- SwiftUI
- UIViewControllerRepresentable
-  dismantleUIViewController(\_:coordinator:) 

Type Method

# dismantleUIViewController(\_:coordinator:)

Cleans up the presented view controller (and coordinator) in anticipation of their removal.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+tvOS 13.0+visionOS 1.0+

``` source
@MainActor @preconcurrency
static func dismantleUIViewController(
    _ uiViewController: Self.UIViewControllerType,
    coordinator: Self.Coordinator
)
```

**Required** Default implementation provided.

## Parameters 

`uiViewController`  

Your custom view controller object.

`coordinator`  

The custom coordinator instance you use to communicate changes back to SwiftUI. If you do not use a custom coordinator, the system provides a default instance.

## Discussion

Use this method to perform additional clean-up work related to your custom view controller. For example, you might use this method to remove observers or update other parts of your SwiftUI interface.

## Default Implementations

### UIViewControllerRepresentable Implementations

static func dismantleUIViewController(Self.UIViewControllerType, coordinator: Self.Coordinator)

Cleans up the presented view controller (and coordinator) in anticipation of their removal.

