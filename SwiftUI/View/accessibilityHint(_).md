- SwiftUI
- View
- accessibilityHint(_:)

Instance Method

# accessibilityHint(_:)

Communicates to the user what happens after performing the view’s action.

iOS 14.0+ iPadOS 14.0+ Mac Catalyst 14.0+ macOS 11.0+ tvOS 14.0+ visionOS 1.0+ watchOS 7.0+

```swift
@export(implementation) nonisolated
func accessibilityHint(_ hint: LocalizedStringResource) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
```

```swift
nonisolated
func accessibilityHint(_ hint: Text) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
```

```swift
nonisolated
func accessibilityHint(_ hintKey: LocalizedStringKey) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
```

```swift
nonisolated
func accessibilityHint<S>(_ hint: S) -> ModifiedContent<Self, AccessibilityAttachmentModifier> where S : StringProtocol
```

## Discussion

...