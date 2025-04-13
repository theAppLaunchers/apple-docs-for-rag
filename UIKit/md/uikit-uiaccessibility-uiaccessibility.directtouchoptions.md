

- UIKit
- UIAccessibility
-  UIAccessibility.DirectTouchOptions 

Structure

# UIAccessibility.DirectTouchOptions

Constants that configure how VoiceOver produces audio for direct touch areas.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
struct DirectTouchOptions
```

## Overview

*Direct touch areas* are regions of the screen where VoiceOver passes gestures directly to the app instead of interpreting them as VoiceOver commands.

Examples of direct touch areas include:

- A keyboard in a music-creation app

- A player view in a game that produces sounds

- An area where you sign your name in a document

If an element doesn’t use `UIAccessibility.DirectTouchOptions`, VoiceOver speaks the element and immediately starts sending touch events to the app.

Specify `DirectTouchOptions` to customize VoiceOver regions using these two constants:

- Use silentOnTouch to ensure VoiceOver is silent when a person touches the direct touch area. In this region, the app produces its own audio feedback without conflicting with VoiceOver audio.

- Use requiresActivation to ensure a person interacts with the user interface element before a touch passes through to the element. This is useful for scenarios where an errant touch may produce undesired input, such as a signature field.

## Topics

### Initializers

init(rawValue: UInt)

Creates a new direct touch options structure using an unsigned integer.

### Type Properties

static var requiresActivation: UIAccessibility.DirectTouchOptions

Inhibits passthrough to the direct touch area until a person double-taps the element.

static var silentOnTouch: UIAccessibility.DirectTouchOptions

Allows a direct touch area to immediately receive touch events without triggering VoiceOver audio.

## Relationships

### Conforms To

- BitwiseCopyable
- Equatable
- ExpressibleByArrayLiteral
- OptionSet
- RawRepresentable
- Sendable
- SetAlgebra

## See Also

### Configuring behavior

@MainActor var accessibilityCustomRotors: [UIAccessibilityCustomRotor]? { get set }

@MainActor var accessibilityElementsHidden: Bool { get set }

@MainActor var accessibilityRespondsToUserInteraction: Bool { get set }

@MainActor var accessibilityViewIsModal: Bool { get set }

@MainActor var shouldGroupAccessibilityChildren: Bool { get set }

@MainActor var accessibilityDirectTouchOptions: UIAccessibility.DirectTouchOptions { get set }

