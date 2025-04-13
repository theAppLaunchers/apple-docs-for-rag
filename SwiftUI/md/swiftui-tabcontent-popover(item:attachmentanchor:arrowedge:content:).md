

- SwiftUI
- TabContent
-  popover(item:attachmentAnchor:arrowEdge:content:) 

Instance Method

# popover(item:attachmentAnchor:arrowEdge:content:)

Presents a popover using the given item as a data source for the popover’s content.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
nonisolated
func popover(
    item: Binding,
    attachmentAnchor: PopoverAttachmentAnchor = .rect(.bounds),
    arrowEdge: Edge? = nil,
    @ViewBuilder content: @escaping (Item) -> Content
) -> some TabContent where Item : Identifiable, Content : View
```

## Parameters 

`item`  

A binding to an optional source of truth for the popover. When `item` is non-`nil`, the system passes the contents to the modifier’s closure. You use this content to populate the fields of a popover that you create that the system displays to the user. If `item` changes, the system dismisses the currently presented popover and replaces it with a new popover using the same process.

`attachmentAnchor`  

The positioning anchor that defines the attachment point of the popover. The default is bounds.

`arrowEdge`  

The edge of the `attachmentAnchor` that defines the location of the popover’s arrow in macOS. The default is Edge.top.

`content`  

A closure returning the content of the popover.

## Discussion

Use this method when you need to present a popover with content from a custom data source. The example below uses data in the `PopoverModel` structure to populate the view in the `content` closure that the popover displays to the user:

```
struct PopoverExample: View {
    @State private var popover: PopoverModel?

    var body: some View {
        TabView {
            Tab("Popover Anchor", systemImage: "arrow.down") {
                Button("Show Popover") {
                    popover = PopoverModel(message: "Custom Message")
                }
            }
            .popover(item: $popover) { detail in
                 Text("\(detail.message)")
                    .padding()
             }
        }
    }
}

struct PopoverModel: Identifiable {
    var id: String { message }
    let message: String
}
```

