

- SwiftUI
- ScrollPosition
-  init(idType:) 

Initializer

# init(idType:)

Creates a new automatic scroll position.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
init(idType: (some Hashable & Sendable).Type = Never.self)
```

## Discussion

You can provide a type to the scroll position. This type should match the type of IDs associated to views in a scroll target layout. The scroll view will look for those views to update the value of the scroll position with.

