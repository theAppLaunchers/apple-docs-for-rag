- SwiftUI
- Toggle

Structure

# Toggle

A control that toggles between on and off states.

iOS 13.0+ iPadOS 13.0+ Mac Catalyst 13.0+ macOS 10.15+ tvOS 13.0+ visionOS 1.0+ watchOS 6.0+

```swift
nonisolated
struct Toggle<Label> where Label : View
```

## Overview

You create a toggle by providing an isOn binding and a label. Bind isOn to a Boolean property that determines whether the toggle is on or off. Set the label to a view that visually describes the purpose of switching between toggle states. For example:

```swift
@State private var vibrateOnRing = false

var body: some View {
    Toggle(isOn: $vibrateOnRing) {
        Text("Vibrate on Ring")
    }
}
```

For the common case of Label based labels, you can use the convenience initializer that takes a title string (or localized string key) and the name of a system image:

```swift
@State private var vibrateOnRing = true

var body: some View {
    Toggle(
        "Vibrate on Ring",
        systemImage: "dot.radiowaves.left.and.right",
        isOn: $vibrateOnRing
    )
}
```

For text-only labels, you can use the convenience initializer that takes a title string (or localized string key) as its first parameter, instead of a trailing closure:

```swift
@State private var vibrateOnRing = true

var body: some View {
    Toggle("Vibrate on Ring", isOn: $vibrateOnRing)
}
```

For cases where adding a subtitle to the label is desired, use a view builder that creates multiple Text views where the first text represents the title and the second text represents the subtitle:

```swift
@State private var vibrateOnRing = false

var body: some View {
    Toggle(isOn: $vibrateOnRing) {
        Text("Vibrate on Ring")
        Text("Enable vibration when the phone rings")
    }
}
```

Note

This behavior does not apply to button.

### Styling toggles

Toggles use a default style that varies based on both the platform and the context. For more information, read about the automatic toggle style.
You can customize the appearance and interaction of toggles by applying styles using the toggleStyle(_:) modifier. You can apply built-in styles, like switch, to either a toggle, or to a view hierarchy that contains toggles:

```swift
VStack {
    Toggle("Vibrate on Ring", isOn: $vibrateOnRing)
    Toggle("Vibrate on Silent", isOn: $vibrateOnSilent)
}
.toggleStyle(.switch)
```

You can also define custom styles by creating a type that conforms to the ToggleStyle protocol.

## Topics

...

## Relationships

### Conforms To

View

## See Also

...