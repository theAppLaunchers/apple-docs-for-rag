Framework

# Symbols

Apply universal animations to symbol-based images.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

## [Overview](/documentation/Symbols#overview)

The Symbols framework provides access to symbol effects you can use to animate [SF Symbols](https://developer.apple.com/design/human-interface-guidelines/sf-symbols) in your AppKit, UIKit, and SwiftUI apps. These animations exhibit different behaviors:

Discrete

An effect that runs from start to finish.

Indefinite

An effect that lasts until you remove or disable it.

Transition

An effect that animates a symbol in or out of visibility.

Content Transition

An effect that replaces one symbol with another symbol, or with a different configuration of itself.

A symbol effect can exhibit multiple types of behavior. For instance, you can add a pulse effect with an option to occur a finite number of times — a discrete behavior. You can also add a pulse effect with an option to loop forever — an indefinite behavior.

```

```
// Add an effect in SwiftUI.
Image(systemName: "globe")
    // Add effect with discrete behavior to image view.
    .symbolEffect(.pulse, options: .repeat(3))
Image(systemName: "globe")
    // Add effect with indefinite behavior to image view.
    .symbolEffect(.pulse)
```

```

You can apply universal animation effects to symbol-based images that you display in image views. The Symbols framework provides a consistent set of effects to use regardless of your UI framework or langauge choices.

Consider a SwiftUI app that displays a variable color effect on a Wi-Fi symbol while the system searches for Wi-Fi networks.

```

```
// Add an effect in SwiftUI.
Image(systemName: "wifi")
    .symbolEffect(.variableColor.reversing)
```

```

Now consider an AppKit or UIKit version of the app. You can apply the same effect to animate the search for Wi-Fi networks.

```

```
// Add an effect in AppKit and UIKit.
imageView.addSymbolEffect(.variableColor.reversing)
```

```

```

```
// Add an effect in AppKit and UIKit.
[self.imageView
  addSymbolEffect:[[NSSymbolVariableColorEffect effect] effectWithReversing]];
```

```

## [Topics](/documentation/Symbols#topics)

### [Symbol effects](/documentation/Symbols#Symbol-effects)

[`static var appear: AppearSymbolEffect`](/documentation/symbols/symboleffect/appear)

An animation that makes the layers of a symbol-based image appear separately or as a whole.

[`static var bounce: BounceSymbolEffect`](/documentation/symbols/symboleffect/bounce)

An animation that applies a transitory scaling effect, or bounce, to the layers in a symbol-based image separately or as a whole.

[`static var disappear: DisappearSymbolEffect`](/documentation/symbols/symboleffect/disappear)

An animation that makes the layers of a symbol-based image disappear separately or as a whole.

[`static var pulse: PulseSymbolEffect`](/documentation/symbols/symboleffect/pulse)

An animation that fades the opacity of some or all layers in a symbol-based image.

[`static var scale: ScaleSymbolEffect`](/documentation/symbols/symboleffect/scale)

An animation that scales the layers in a symbol-based image separately or as a whole.

[`static var variableColor: VariableColorSymbolEffect`](/documentation/symbols/symboleffect/variablecolor)

An animation that replaces the opacity of variable layers in a symbol-based image in a repeatable sequence.

### [Symbol content transitions](/documentation/Symbols#Symbol-content-transitions)

[`static var replace: ReplaceSymbolEffect`](/documentation/symbols/symboleffect/replace)

An animation that replaces the layers of one symbol-based image with those of another.

[`static var automatic: AutomaticSymbolEffect`](/documentation/symbols/symboleffect/automatic)

A transition that applies the default animation to a symbol-based image in a context-sensitive manner.

### [Symbol effect types](/documentation/Symbols#Symbol-effect-types)

```swift
```swift
```swift
```swift
struct AppearSymbolEffect
```
```

A type that makes the layers of a symbol-based image appear separately or as a whole.
```
```swift
```swift
```swift
struct AutomaticSymbolEffect
```
```

A type that applies the default animation to a symbol-based image in a context-sensitive manner.
```
```swift
```swift
```swift
struct BounceSymbolEffect
```
```

A type that applies a transitory scaling effect, or bounce, to the layers in a symbol-based image separately or as a whole.
```
```swift
```swift
```swift
struct DisappearSymbolEffect
```
```

A type that makes the layers of a symbol-based image disappear separately or as a whole.
```
```swift
```swift
```swift
struct PulseSymbolEffect
```
```

A type that fades the opacity of some or all layers in a symbol-based image.
```
```swift
```swift
```swift
struct ReplaceSymbolEffect
```
```

A type that replaces the layers of one symbol-based image with those of another.
```
```swift
```swift
```swift
struct ScaleSymbolEffect
```
```

A type that scales the layers in a symbol-based image separately or as a whole.
```
```swift
```swift
```swift
struct VariableColorSymbolEffect
```
```

A type that replaces the opacity of variable layers in a symbol-based image in a repeatable sequence.
```
```swift
```swift
```swift
struct BreatheSymbolEffect
```
```
```
```swift
```swift
```swift
struct RotateSymbolEffect
```
```
```
```swift
```swift
```swift
struct WiggleSymbolEffect
```
```
```
```

### [Symbol effect options](/documentation/Symbols#Symbol-effect-options)

```swift
```swift
```swift
```swift
struct SymbolEffectOptions
```
```

Options that configure how effects apply to symbol-based images.
```
```

### [Symbol effect protocols](/documentation/Symbols#Symbol-effect-protocols)

```swift
```swift
```swift
```swift
protocol SymbolEffect
```
```

A presentation effect that you apply to a symbol-based image.
```
```swift
```swift
```swift
protocol DiscreteSymbolEffect
```
```

An effect that performs a transient animation.
```
```swift
```swift
```swift
protocol IndefiniteSymbolEffect
```
```

An animation that continually affects a symbol until it’s disabled or removed.
```
```swift
```swift
```swift
protocol ContentTransitionSymbolEffect
```
```

An effect that animates between symbols or different configurations of the same symbol.
```
```swift
```swift
```swift
protocol TransitionSymbolEffect
```
```

An effect that animates a symbol in or out.
```
```

### [Structures](/documentation/Symbols#Structures)

```swift
```swift
```swift
```swift
struct DrawOffSymbolEffect
```
```

A symbol effect that applies the DrawOff animation to symbol images.
```
```swift
```swift
```swift
struct DrawOnSymbolEffect
```
```

A symbol effect that applies the DrawOn animation to symbol images.
```
```