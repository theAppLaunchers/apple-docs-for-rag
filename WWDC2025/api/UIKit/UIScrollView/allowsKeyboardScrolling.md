*   [UIKit](/documentation/uikit)
*   [UIScrollView](/documentation/uikit/uiscrollview)
*   allowsKeyboardScrolling

Instance Property

# allowsKeyboardScrolling

A Boolean value that determines whether the scroll view allows scrolling its content with hardware keyboard input.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
var allowsKeyboardScrolling: [`Bool`](/documentation/Swift/Bool) { get set }
```

```
```
```
```
```
```
```

## [Discussion](/documentation/UIKit/UIScrollView/allowsKeyboardScrolling#Discussion)

When this value is [`true`](/documentation/swift/true), the scroll view animates its content offset in response to input from hardware keyboard keys like Page Up, Page Down, Home, End, and the arrow keys. The scroll view needs to have focus or be first responder to receive these key events.

The default value is [`true`](/documentation/swift/true) for apps that link against iOS 17 and later. Set this value to [`false`](/documentation/swift/false) to disable the ability to scroll content with hardware keyboard keys.