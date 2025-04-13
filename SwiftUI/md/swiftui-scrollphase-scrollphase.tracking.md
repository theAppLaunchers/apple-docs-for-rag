

- SwiftUI
- ScrollPhase
-  ScrollPhase.tracking 

Case

# ScrollPhase.tracking

The tracking phase where the scroll view is tracking a potential scroll by the user but the user hasn’t started a scroll.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
case tracking
```

## Discussion

For example, on iOS, the user may start touching content inside of the scroll view. Until the user moves their finger the scroll view would be tracking the the finger. Not all platforms or kinds of scroll may trigger this phase.

## See Also

### Getting scroll gesture states

case animating

The animating phase where the scroll view is animating towards a final target.

case decelerating

The decelerating phase where the user use has stopped interacting with the scroll view and the scroll view is decelerating towards its final target.

case idle

The idle phase where no kind of scrolling is occurring.

case interacting

The interacting phase where the user is interacting with the scroll view.

