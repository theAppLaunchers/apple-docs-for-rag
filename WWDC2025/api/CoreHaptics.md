Framework

# Core Haptics

Compose and play haptic patterns to customize your iOS app’s haptic feedback.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+tvOS 14.0+visionOS 1.0+

## [Overview](/documentation/CoreHaptics#overview)

Core Haptics lets you add customized haptic and audio feedback to your app. Use haptics to engage users physically, with tactile and audio feedback that gets attention and reinforces actions. Some system-provided interface elements—like pickers, switches, and sliders—automatically provide haptic feedback as users interact with them. With Core Haptics, you extend this functionality by composing and combining haptics beyond the default patterns.

Your app can play custom haptic patterns crafted from basic building blocks called haptic events ([`CHHapticEvent`](/documentation/corehaptics/chhapticevent)). Events can be transient, like the feedback you get from toggling a switch, or continuous, like the vibration or sound from a ringtone. You can use transient and continuous patterns independently, or build your pattern from precise combinations of the two. Another type of haptic event allows you to play customized audio content as part of your pattern.

## [Topics](/documentation/CoreHaptics#topics)

### [Essentials](/documentation/CoreHaptics#Essentials)

[

Preparing your app to play haptics](/documentation/corehaptics/preparing-your-app-to-play-haptics)

Set up your app to play haptics.

[

Playing a single-tap haptic pattern](/documentation/corehaptics/playing-a-single-tap-haptic-pattern)

Create and play a transient haptic pattern from a dictionary literal inline.

```swift
```swift
```swift
class CHHapticEngine
```
```

An object that represents the connection to the haptic server.
```
```swift
```swift
```swift
class CHHapticPattern
```
```

An object representing a haptic waveform.
```
```swift
```swift
```swift
protocol CHHapticPatternPlayer
```
```

A protocol that defines a standard pattern player capable of playing haptic patterns with fixed parameters.
```
```swift
```swift
```swift
protocol CHHapticAdvancedPatternPlayer
```
```

A protocol that defines an advanced pattern player capable of looping, seeking, pausing, and resuming haptic playback.
```

### [Programmatic haptics](/documentation/CoreHaptics#Programmatic-haptics)

You can synthesize haptics by configuring parameters like haptic intensity and sharpness. Event parameters define the initial state, while dynamic parameters change the pattern during playback.

[

Delivering Rich App Experiences with Haptics](/documentation/corehaptics/delivering-rich-app-experiences-with-haptics)

Enhance your app’s experience by incorporating haptic and sound feedback into key interactive moments.

[

Playing Collision-Based Haptic Patterns](/documentation/corehaptics/playing-collision-based-haptic-patterns)

Play a custom haptic pattern whose strength depends on an object’s collision speed.

[

Updating Continuous and Transient Haptic Parameters in Real Time](/documentation/corehaptics/updating-continuous-and-transient-haptic-parameters-in-real-time)

Generate continuous and transient haptic patterns in response to user touch.

```swift
```swift
```swift
class CHHapticEvent
```
```

An object that describes a single haptic or audio event.
```
```swift
```swift
```swift
class CHHapticEventParameter
```
```

A static parameter value that represents a single property of the haptic pattern.
```
```swift
```swift
```swift
class CHHapticDynamicParameter
```
```

A value that you send to a haptic pattern player to alter a property value during playback.
```
```swift
```swift
```swift
class CHHapticParameterCurve
```
```

A curve that you send to a haptic pattern player to alter a property value gradually during playback.
```

### [File-based haptics](/documentation/CoreHaptics#File-based-haptics)

Apple Haptic and Audio Pattern (AHAP) files are a JSON-like representation of synced haptics and audio that you can load and play from disk.

[

Playing a Custom Haptic Pattern from a File](/documentation/corehaptics/playing-a-custom-haptic-pattern-from-a-file)

Sample predesigned Apple Haptic Audio Pattern files, and learn how to play your own.

[

Representing haptic patterns in AHAP files](/documentation/corehaptics/representing-haptic-patterns-in-ahap-files)

Understand the Apple Haptic and Audio Pattern (AHAP) file format.

### [Game controller haptics](/documentation/CoreHaptics#Game-controller-haptics)

[

Playing Haptics on Game Controllers](/documentation/corehaptics/playing-haptics-on-game-controllers)

Add haptic feedback to supported game controllers by using Core Haptics.

### [Haptic errors](/documentation/CoreHaptics#Haptic-errors)

```swift
```swift
```swift
```swift
let CoreHapticsErrorDomain: String
```
```

A string representation of the haptic error domain.
```
```swift
```swift
```swift
struct CHHapticError
```
```

A structure that represents a framework error.
```
```swift
```swift
```swift
enum Code
```
```

Error codes for framework operations.
```
```

### [Variables](/documentation/CoreHaptics#Variables)

```swift
```swift
```swift
```swift
let CHHapticAudioResourceKeyLoopEnabled: String
```
```

A key for a Boolean value that indicates whether to loop audio playback.
```
```swift
```swift
```swift
let CHHapticAudioResourceKeyUseVolumeEnvelope: String
```
```

A key for a Boolean value that indicates whether audio file playback fades in and out using an envelope.
```
```

### [Type Aliases](/documentation/CoreHaptics#Type-Aliases)

```swift
```swift
```swift
```swift
typealias CHHapticAudioResourceKey
```
```

A type alias for a key that identifies the playback behavior of an audio resource.
```
```