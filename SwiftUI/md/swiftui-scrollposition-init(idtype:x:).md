

- SwiftUI
- ScrollPosition
-  init(idType:x:) 

Initializer

# init(idType:x:)

Creates a new scroll position to be scrolled to the provided y value.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
init(
    idType: (some Hashable & Sendable).Type = Never.self,
    x: CGFloat
)
```

## Discussion

You can provide a type to the scroll position. This type should match the type of IDs associated to views in a scroll target layout. The scroll view will look for those views to update the value of the scroll position with.

