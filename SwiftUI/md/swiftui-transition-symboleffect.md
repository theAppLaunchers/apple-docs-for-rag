

- SwiftUI
- Transition
-  symbolEffect 

Type Property

# symbolEffect

A transition that applies the default symbol effect transition to symbol images within the inserted or removed view hierarchy. Other views are unaffected by this transition.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
@MainActor @preconcurrency
static var symbolEffect: SymbolEffectTransition { get }
```

Available when `Self` is `SymbolEffectTransition`.

## See Also

### Getting built-in transitions

static var blurReplace: BlurReplaceTransition

A transition that animates the insertion or removal of a view by combining blurring and scaling effects.

static func blurReplace(BlurReplaceTransition.Configuration) -> Self

A transition that animates the insertion or removal of a view by combining blurring and scaling effects.

static var identity: IdentityTransition

A transition that returns the input view, unmodified, as the output view.

static func move(edge: Edge) -> Self

Returns a transition that moves the view away, towards the specified edge of the view.

static func offset(CGSize) -> Self

Returns a transition that offset the view by the specified amount.

static func offset(x: CGFloat, y: CGFloat) -> Self

Returns a transition that offset the view by the specified x and y values.

static var opacity: OpacityTransition

A transition from transparent to opaque on insertion, and from opaque to transparent on removal.

static func push(from: Edge) -> Self

Creates a transition that when added to a view will animate the view’s insertion by moving it in from the specified edge while fading it in, and animate its removal by moving it out towards the opposite edge and fading it out.

static var scale: ScaleTransition

Returns a transition that scales the view.

static func scale(Double, anchor: UnitPoint) -> Self

Returns a transition that scales the view by the specified amount.

static var slide: SlideTransition

A transition that inserts by moving in from the leading edge, and removes by moving out towards the trailing edge.

static func symbolEffect&lt;T>(T, options: SymbolEffectOptions) -> SymbolEffectTransition

Creates a transition that applies the provided effect to symbol images within the inserted or removed view hierarchy. Other views are unaffected by this transition.

