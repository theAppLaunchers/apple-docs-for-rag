- SwiftUI
- View
- accessibilityLabel(_:)

Instance Method

# accessibilityLabel(_:)

Adds a label to the view that describes its contents.

iOS 14.0+ iPadOS 14.0+ Mac Catalyst 14.0+ macOS 11.0+ tvOS 14.0+ visionOS 1.0+ watchOS 7.0+

```swift
@export(implementation) nonisolated
func accessibilityLabel(_ label: LocalizedStringResource) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
```

```swift
nonisolated
func accessibilityLabel(_ label: Text) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
```

```swift
nonisolated
func accessibilityLabel(_ labelKey: LocalizedStringKey) -> ModifiedContent<Self, AccessibilityAttachmentModifier>
```

```swift
nonisolated
func accessibilityLabel<S>(_ label: S) -> ModifiedContent<Self, AccessibilityAttachmentModifier> where S : StringProtocol
```

## Discussion

...