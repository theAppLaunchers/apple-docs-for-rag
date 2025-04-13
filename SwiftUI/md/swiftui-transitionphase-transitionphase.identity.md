

- SwiftUI
- TransitionPhase
-  TransitionPhase.identity 

Case

# TransitionPhase.identity

The transition is being applied to a view that is in the view hierarchy.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
case identity
```

## Discussion

In this phase, a transition should show its steady state appearance, which will generally not make any visual change to the view.

## See Also

### Getting the phase

case willAppear

The transition is being applied to a view that is about to be inserted into the view hierarchy.

case didDisappear

The transition is being applied to a view that has been requested to be removed from the view hierarchy.

