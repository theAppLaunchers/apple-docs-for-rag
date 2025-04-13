

- SwiftUI
- ScrollPosition
-  scrollTo(x:) 

Instance Method

# scrollTo(x:)

Scrolls the position of the scroll view to the x value you provide.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
mutating func scrollTo(x: CGFloat)
```

## Discussion

The scroll view chooses the y value based on the content insets of the scroll view and will clamp this value to only scroll to the size of its actual content.

