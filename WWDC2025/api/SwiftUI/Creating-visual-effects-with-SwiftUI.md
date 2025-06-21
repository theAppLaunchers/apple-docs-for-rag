*   [SwiftUI](/documentation/swiftui)
*   [Text input and output](/documentation/swiftui/text-input-and-output)
*   Creating visual effects with SwiftUI

Sample Code

# Creating visual effects with SwiftUI

Add scroll effects, rich color treatments, custom transitions, and advanced effects using shaders and a text renderer.

[Download](https://docs-assets.developer.apple.com/published/9a15b1cc1a22/CreatingVisualEffectsWithSwiftUI.zip)

iOS 18.0+iPadOS 18.0+Xcode 16.0+

## [Overview](/documentation/SwiftUI/Creating-visual-effects-with-SwiftUI#Overview)

Note

This sample code project is associated with WWDC24 session 10151: [Create custom visual effects in SwiftUI](https://developer.apple.com/wwdc24/10151/).

## [See Also](/documentation/SwiftUI/Creating-visual-effects-with-SwiftUI#see-also)

### [Rendering text](/documentation/SwiftUI/Creating-visual-effects-with-SwiftUI#Rendering-text)

```swift
```swift
```swift
```swift
protocol TextAttribute
```
```

A value that you can attach to text views and that text renderers can query.
```
```swift
```swift
```swift
func textRenderer<T>(T) -> some View
```
```

Returns a new view such that any text views within it will use `renderer` to draw themselves.
```
```swift
```swift
```swift
protocol TextRenderer
```
```

A value that can replace the default text view rendering behavior.
```
```swift
```swift
```swift
struct TextProxy
```
```

A proxy for a text view that custom text renderers use.
```
```