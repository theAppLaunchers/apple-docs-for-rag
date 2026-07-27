- SwiftUI
- Slider

Structure

# Slider

A control for selecting a value from a bounded linear range of values.

iOS 13.0+ iPadOS 13.0+ Mac Catalyst 13.0+ macOS 10.15+ visionOS 1.0+ watchOS 6.0+

```swift
nonisolated
struct Slider<Label, ValueLabel> where Label : View, ValueLabel : View
```

## Overview

A slider consists of a “thumb” image that the user moves between two extremes of a linear “track”. The ends of the track represent the minimum and maximum possible values. As the user moves the thumb, the slider updates its bound value.

The following example shows a slider bound to the value speed. As the slider updates this value, a bound Text view shows the value updating. The onEditingChanged closure passed to the slider receives callbacks when the user drags the slider. The example uses this to change the color of the value text.

```swift
@State private var speed = 50.0
@State private var isEditing = false

var body: some View {
    VStack {
        Slider(
            value: $speed,
            in: 0...100,
            onEditingChanged: { editing in
                isEditing = editing
            }
        )
        Text("\(speed)")
            .foregroundColor(isEditing ? .red : .blue)
    }
}
```

You can also use a step parameter to provide incremental steps along the path of the slider. For example, if you have a slider with a range of 0 to 100, and you set the step value to 5, the slider’s increments would be 0, 5, 10, and so on. The following example shows this approach, and also adds optional minimum and maximum value labels.

```swift
@State private var speed = 50.0
@State private var isEditing = false

var body: some View {
    Slider(
        value: $speed,
        in: 0...100,
        step: 5
    ) {
        Text("Speed")
    } minimumValueLabel: {
        Text("0")
    } maximumValueLabel: {
        Text("100")
    } onEditingChanged: { editing in
        isEditing = editing
    }
    Text("\(speed)")
        .foregroundColor(isEditing ? .red : .blue)
}
```

The slider also uses the step to increase or decrease the value when a VoiceOver user adjusts the slider with voice commands.

## Topics

...

## Relationships

### Conforms To

View

## See Also

...