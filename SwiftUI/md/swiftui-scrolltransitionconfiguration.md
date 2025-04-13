

- SwiftUI
-  ScrollTransitionConfiguration 

Structure

# ScrollTransitionConfiguration

The configuration of a scroll transition that controls how a transition is applied as a view is scrolled through the visible region of a containing scroll view or other container.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
struct ScrollTransitionConfiguration
```

## Topics

### Getting the configuration

static let identity: ScrollTransitionConfiguration

Creates a new configuration that does not change the appearance of the view.

static let animated: ScrollTransitionConfiguration

Creates a new configuration that discretely animates the transition when the view becomes visible.

static func animated(Animation) -> ScrollTransitionConfiguration

Creates a new configuration that discretely animates the transition when the view becomes visible.

static let interactive: ScrollTransitionConfiguration

Creates a new configuration that interactively interpolates the transition’s effect as the view is scrolled into the visible region of the container.

static func interactive(timingCurve: UnitCurve) -> ScrollTransitionConfiguration

Creates a new configuration that interactively interpolates the transition’s effect as the view is scrolled into the visible region of the container.

### Accessing the configuration

func animation(Animation) -> ScrollTransitionConfiguration

Sets the animation with which the transition will be applied.

func threshold(ScrollTransitionConfiguration.Threshold) -> ScrollTransitionConfiguration

Sets the threshold at which the view will be considered fully visible.

struct Threshold

Describes a specific point in the progression of a target view within a container from hidden (fully outside the container) to visible.

## See Also

### Animating scroll transitions

func scrollTransition(ScrollTransitionConfiguration, axis: Axis?, transition: (EmptyVisualEffect, ScrollTransitionPhase) -> some VisualEffect) -> some View

Applies the given transition, animating between the phases of the transition as this view appears and disappears within the visible region of the containing scroll view, or other container specified using the `coordinateSpace` parameter.

func scrollTransition(topLeading: ScrollTransitionConfiguration, bottomTrailing: ScrollTransitionConfiguration, axis: Axis?, transition: (EmptyVisualEffect, ScrollTransitionPhase) -> some VisualEffect) -> some View

Applies the given transition, animating between the phases of the transition as this view appears and disappears within the visible region of the containing scroll view, or other container specified using the `coordinateSpace` parameter.

enum ScrollTransitionPhase

The phases that a view transitions between when it scrolls among other views.

