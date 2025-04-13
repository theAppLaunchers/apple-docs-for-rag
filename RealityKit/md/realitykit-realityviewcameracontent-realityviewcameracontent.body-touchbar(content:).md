

- RealityKit
- RealityViewCameraContent
- RealityViewCameraContent.Body
-  touchBar(content:) 

Instance Method

# touchBar(content:)

Sets the content that the Touch Bar displays.

RealityKitSwiftUImacOS 10.15+

``` source
nonisolated
func touchBar(@ViewBuilder content: () -> Content) -> some View where Content : View
```

## Parameters 

`content`  

A collection of views to be displayed by the Touch Bar.

## Return Value

A view that contains the Touch Bar content.

## Discussion

Use `touchBar(_:)` when you need to dynamically construct items to show in the Touch Bar. The content is displayed by the Touch Bar when appropriate, depending on focus.

In the example below, four buttons are added to a Touch Bar content struct and then added to the Touch Bar:

```
let touchBarItems = TouchBar(id: "myBarItems") {
    Button("♣️", action: {})
    Button("♥️", action: {})
    Button("♠️", action: {})
    Button("♦️", action: {})
}

TextField("TouchBar Demo", text: $placeholder)
    .frame(maxWidth: .infinity, maxHeight: .infinity)
    .focusable()
    .touchBar(touchBarItems)
```

