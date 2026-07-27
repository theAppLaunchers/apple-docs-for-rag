- SwiftUI
- View
- sheet(isPresented:onDismiss:content:)

Instance Method

# sheet(isPresented:onDismiss:content:)

Presents a sheet when a binding to a Boolean value that you provide is true.

iOS 13.0+ iPadOS 13.0+ Mac Catalyst 13.0+ macOS 10.15+ tvOS 13.0+ visionOS 1.0+ watchOS 6.0+

```swift
nonisolated
func sheet<Content>(
    isPresented: Binding<Bool>,
    onDismiss: (() -> Void)? = nil,
    @ContentBuilder content: @escaping () -> Content
) -> some View where Content : View
```

## Parameters

isPresented

A binding to a Boolean value that determines whether to present the sheet that you create in the modifier’s content closure.

onDismiss

The closure to execute when dismissing the sheet.

content

A closure that returns the content of the sheet.

## Discussion

...

## See also

...