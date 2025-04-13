

- RealityKit
- Model3DPlaceholderContent
-  popover(isPresented:attachmentAnchor:arrowEdge:content:) 

Instance Method

# popover(isPresented:attachmentAnchor:arrowEdge:content:)

Presents a popover when a given condition is true.

RealityKitSwiftUIiOS 13.0+iPadOS 13.0+macOS 10.15+visionOS

``` source
nonisolated
func popover(
    isPresented: Binding,
    attachmentAnchor: PopoverAttachmentAnchor = .rect(.bounds),
    arrowEdge: Edge? = nil,
    @ViewBuilder content: @escaping () -> Content
) -> some View where Content : View
```

## Parameters 

`isPresented`  

A binding to a Boolean value that determines whether to present the popover content that you return from the modifier’s `content` closure.

`attachmentAnchor`  

The positioning anchor that defines the attachment point of the popover. The default is `Anchor/Source/bounds`.

`arrowEdge`  

The edge of the `attachmentAnchor` that defines the location of the popover’s arrow. The default is `nil`, which results in the system allowing any arrow edge.

`content`  

A closure returning the content of the popover.

## Discussion

Use this method to show a popover whose contents are a SwiftUI view that you provide when a bound Boolean variable is `true`. In the example below, a popover displays whenever the user toggles the `isShowingPopover` state variable by pressing the “Show Popover” button:

```
struct PopoverExample: View {
    @State private var isShowingPopover = false

    var body: some View {
        Button("Show Popover") {
            self.isShowingPopover = true
        }
        .popover(
            isPresented: $isShowingPopover, arrowEdge: .bottom
        ) {
            Text("Popover Content")
                .padding()
        }
    }
}
```

Important

Prior to iOS 18.1, the popover arrow edge was not respected. Apps that are re-compiled with the iOS 18.1 or later SDK or visionOS 2.1 or later SDK and run on iOS 18.1 or later or visionOS 2.1 or later have the arrow edge respected. On macOS, arrow edge has always been respected. Alternatively, to allow the system to choose the best orientation of the popover’s arrow, use the `View/popover(isPresented:attachmentAnchor:content:)` variant.

