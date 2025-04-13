

- SwiftUI
- View
-  tint(\_:) 

Instance Method

# tint(\_:)

Sets the tint color within this view.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
nonisolated
func tint(_ tint: Color?) -> some View
```

Show all declarations

## Parameters 

`tint`  

The tint Color to apply.

## Discussion

Use this method to override the default accent color for this view. Unlike an app’s accent color, which can be overridden by user preference, the tint color is always respected and should be used as a way to provide additional meaning to the control.

This example shows Answer and Decline buttons with green and red tint colors, respectively.

```
struct ControlTint: View {
    var body: some View {
        HStack {
            Button {
                // Answer the call
            } label: {
                Label("Answer", systemImage: "phone")
            }
            .tint(.green)
            Button {
                // Decline the call
            } label: {
                Label("Decline", systemImage: "phone.down")
            }
            .tint(.red)
        }
        .buttonStyle(.borderedProminent)
        .padding()
    }
}
```

Some controls adapt to the tint color differently based on their style, the current platform, and the surrounding context. For example, in macOS, a button with the bordered style doesn’t tint its background, but one with the borderedProminent style does. In macOS, neither of these button styles tint their label, but they do in other platforms.

## See Also

### Setting a color

struct Color

A representation of a color that adapts to a given context.

