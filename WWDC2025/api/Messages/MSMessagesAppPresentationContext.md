*   [Messages](/documentation/messages)
*   MSMessagesAppPresentationContext

Enumeration

# MSMessagesAppPresentationContext

Presentation contexts describing where your iMessage app appears.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
enum MSMessagesAppPresentationContext
```
```
```
```
```
```
```
```

## [Topics](/documentation/Messages/MSMessagesAppPresentationContext#topics)

### [Presentation Contexts](/documentation/Messages/MSMessagesAppPresentationContext#Presentation-Contexts)

[`case media`](/documentation/messages/msmessagesapppresentationcontext/media)

A constant that indicates the iMessage app appears inside the Stickers app throughout iOS including in Messages, FaceTime, the emoji keyboard, and Markup.

[`case messages`](/documentation/messages/msmessagesapppresentationcontext/messages)

A constant that indicates the iMessage app appears in Messages in the list of iMessage apps that appears when you press the plus button.

### [Initializers](/documentation/Messages/MSMessagesAppPresentationContext#Initializers)

[`init?(rawValue: UInt)`](/documentation/messages/msmessagesapppresentationcontext/init\(rawvalue:\))

## [Relationships](/documentation/Messages/MSMessagesAppPresentationContext#relationships)

### [Conforms To](/documentation/Messages/MSMessagesAppPresentationContext#conforms-to)

*   [`BitwiseCopyable`](/documentation/Swift/BitwiseCopyable)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`RawRepresentable`](/documentation/Swift/RawRepresentable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/Messages/MSMessagesAppPresentationContext#see-also)

### [Working with Presentation Styles and Contexts](/documentation/Messages/MSMessagesAppPresentationContext#Working-with-Presentation-Styles-and-Contexts)

```swift
```swift
```swift
```swift
var presentationStyle: MSMessagesAppPresentationStyle
```
```

The extension’s current presentation style.
```
```swift
```swift
```swift
func requestPresentationStyle(MSMessagesAppPresentationStyle)
```
```

Asks the extension’s user interface to transition to the provided style.
```
```swift
```swift
```swift
func willTransition(to: MSMessagesAppPresentationStyle)
```
```

Tells the view controller that the extension is about to transition to a new presentation style.
```
```swift
```swift
```swift
func didTransition(to: MSMessagesAppPresentationStyle)
```
```

Tells the view controller that the extension has transitioned to a new presentation style.
```
```swift
```swift
```swift
enum MSMessagesAppPresentationStyle
```
```

Presentation styles that describe your iMessage app’s appearance.
```
```swift
```swift
```swift
var presentationContext: MSMessagesAppPresentationContext
```
```

The context describing where your iMessage app is presented.
```
```