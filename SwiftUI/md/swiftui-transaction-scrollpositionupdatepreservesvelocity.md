

- SwiftUI
- Transaction
-  scrollPositionUpdatePreservesVelocity 

Instance Property

# scrollPositionUpdatePreservesVelocity

Whether a programmatic update to the scroll position of a scroll view preserves the current velocity of any active scroll of the scroll view.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
var scrollPositionUpdatePreservesVelocity: Bool { get set }
```

## Discussion

By default, when a scroll view sees a programmatic update to its scroll position, it will stop any active scrolls for unanimated scrolls. If a programmatic update is animated, this property is ignored.

