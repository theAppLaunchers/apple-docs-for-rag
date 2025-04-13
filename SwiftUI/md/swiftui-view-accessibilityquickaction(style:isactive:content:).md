

- SwiftUI
- View
-  accessibilityQuickAction(style:isActive:content:) 

Instance Method

# accessibilityQuickAction(style:isActive:content:)

Adds a quick action to be shown by the system when active.

watchOS 9.0+

``` source
nonisolated
func accessibilityQuickAction(
    style: Style,
    isActive: Binding,
    @ViewBuilder content: () -> Content
) -> some View where Style : AccessibilityQuickActionStyle, Content : View
```

## Discussion

The following example shows how to add a quick action to pause and resume a workout, with the prompt style.

```
@State private var isPaused = false
@State private var isQuickActionActive = false

var body: some View {
    WorkoutView(isPaused: $isPaused)
        .accessibilityQuickAction(style: .prompt, isActive: $isQuickActionActive) {
            Button(isPaused ? "Resume" : "Pause") {
                isPaused.toggle()
            }
        }
}
```

The following example shows how to add a quick action to play and pause music, with the outline style.

```
@State private var isPlaying = false
@State private var isQuickActionActive = false

var body: some View {
    PlayButton(isPlaying: $isPlaying)
        .contentShape(.focusEffect, Circle())
        .accessibilityQuickAction(style: .outline, isActive: $isQuickActionActive) {
            Button(isPlaying ? "Pause" : "Play") {
                isPlaying.toggle()
            }
        }
}
```

## See Also

### Offering Quick Actions to people

func accessibilityQuickAction&lt;Style, Content>(style: Style, content: () -> Content) -> some View

Adds a quick action to be shown by the system when active.

protocol AccessibilityQuickActionStyle

A type that describes the presentation style of an accessibility quick action.

