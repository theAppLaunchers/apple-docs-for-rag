

- RealityKit
- Model3DPlaceholderContent
-  controlSize(\_:) 

Instance Method

# controlSize(\_:)

Sets the size for controls within this view.

RealityKitSwiftUIiOS 15.0+iPadOS 15.0+macOS 10.15+visionOSwatchOS 9.0+

``` source
nonisolated
func controlSize(_ controlSize: ControlSize) -> some View
```

## Parameters 

`controlSize`  

One of the control sizes specified in the `ControlSize` enumeration.

## Discussion

Use `controlSize(_:)` to override the system default size for controls in this view. In this example, a view displays several typical controls at `.mini`, `.small` and `.regular` sizes.

```
struct ControlSize: View {
    var body: some View {
        VStack {
            MyControls(label: "Mini")
                .controlSize(.mini)
            MyControls(label: "Small")
                .controlSize(.small)
            MyControls(label: "Regular")
                .controlSize(.regular)
        }
        .padding()
        .frame(width: 450)
        .border(Color.gray)
    }
}

struct MyControls: View {
    var label: String
    @State private var value = 3.0
    @State private var selected = 1
    var body: some View {
        HStack {
            Text(label + ":")
            Picker("Selection", selection: $selected) {
                Text("option 1").tag(1)
                Text("option 2").tag(2)
                Text("option 3").tag(3)
            }
            Slider(value: $value, in: 1...10)
            Button("OK") { }
        }
    }
}
```

