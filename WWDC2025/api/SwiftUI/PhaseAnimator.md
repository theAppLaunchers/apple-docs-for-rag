*   [SwiftUI](/documentation/swiftui)
*   PhaseAnimator

Structure

# PhaseAnimator

A container that animates its content by automatically cycling through a collection of phases that you provide, each defining a discrete step within an animation.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct PhaseAnimator<Phase, Content> where Phase : [`Equatable`](/documentation/Swift/Equatable), Content : [`View`](/documentation/swiftui/view)
```
```
```
```
```
```
```
```

## [Overview](/documentation/SwiftUI/PhaseAnimator#overview)

Use one of the phase animator view modifiers like [`phaseAnimator(_:content:animation:)`](/documentation/swiftui/view/phaseanimator\(_:content:animation:\)) to create a phased animation in your app.

## [Topics](/documentation/SwiftUI/PhaseAnimator#topics)

### [Creating a phase animator](/documentation/SwiftUI/PhaseAnimator#Creating-a-phase-animator)

[`init(some Sequence<Phase>, content: (Phase) -> Content, animation: (Phase) -> Animation?)`](/documentation/swiftui/phaseanimator/init\(_:content:animation:\))

Cycles through a sequence of phases continuously, animating updates to a view on each phase change.

[`init(some Sequence<Phase>, trigger: some Equatable, content: (Phase) -> Content, animation: (Phase) -> Animation?)`](/documentation/swiftui/phaseanimator/init\(_:trigger:content:animation:\))

Cycles through a sequence of phases in response to changes in a specified value, animating updates to a view on each phase change.

## [Relationships](/documentation/SwiftUI/PhaseAnimator#relationships)

### [Conforms To](/documentation/SwiftUI/PhaseAnimator#conforms-to)

*   [`View`](/documentation/swiftui/view)

## [See Also](/documentation/SwiftUI/PhaseAnimator#see-also)

### [Creating phase-based animation](/documentation/SwiftUI/PhaseAnimator#Creating-phase-based-animation)

[

Controlling the timing and movements of your animations](/documentation/swiftui/controlling-the-timing-and-movements-of-your-animations)

Build sophisticated animations that you control using phase and keyframe animators.

```swift
```swift
```swift
func phaseAnimator<Phase>(some Sequence, content: (PlaceholderContentView<Self>, Phase) -> some View, animation: (Phase) -> Animation?) -> some View
```
```

Animates effects that you apply to a view over a sequence of phases that change continuously.
```
```swift
```swift
```swift
func phaseAnimator<Phase>(some Sequence, trigger: some Equatable, content: (PlaceholderContentView<Self>, Phase) -> some View, animation: (Phase) -> Animation?) -> some View
```
```

Animates effects that you apply to a view over a sequence of phases that change based on a trigger.
```