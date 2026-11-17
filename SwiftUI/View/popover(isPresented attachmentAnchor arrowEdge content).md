- SwiftUI
- View
- popover(isPresented:attachmentAnchor:arrowEdge:content:)

Instance Method

# popover(isPresented:attachmentAnchor:arrowEdge:content:)

Presents a popover when a given condition is true.

iOS 13.0+ iPadOS 13.0+ Mac Catalyst 13.0+ macOS 10.15+ visionOS 1.0+

```swift
@export(implementation) nonisolated
func popover<Content>(
    isPresented: Binding<Bool>,
    attachmentAnchor: PopoverAttachmentAnchor = .rect(.bounds),
    arrowEdge: Edge? = nil,
    @ContentBuilder content: @escaping () -> Content
) -> some View where Content : View
```

## Parameters

isPresented

A binding to a Boolean value that determines whether to present the popover content that you return from the modifier’s content closure.

attachmentAnchor

The positioning anchor that defines the attachment point of the popover. The default is bounds.
arrowEdge

The edge of the attachmentAnchor that defines the location of the popover’s arrow. The default is nil, which results in the system allowing any arrow edge.

content

A closure returning the content of the popover.

## Discussion

...

## See also

...