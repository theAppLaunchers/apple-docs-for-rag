- SwiftUI
- View
- accessibilityValue(_:)

Instance Method

# accessibilityValue(_:)

Adds a textual description of the value that the view contains.

iOS 14.0+ iPadOS 14.0+ Mac Catalyst 14.0+ macOS 11.0+ tvOS 14.0+ visionOS 1.0+ watchOS 7.0+

```swift
@export(implementation) nonisolated
func accessibilityValue(_ valueResource: LocalizedStringResource) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
```

```swift
nonisolated
func accessibilityValue(_ valueDescription: Text) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
```

```swift
nonisolated
func accessibilityValue(_ valueKey: LocalizedStringKey) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
```

```swift
nonisolated
func accessibilityValue<S>(_ value: S) -> ModifiedContent<Self, AccessibilityAttachmentModifier> where S : StringProtocol
```

## Discussion

...