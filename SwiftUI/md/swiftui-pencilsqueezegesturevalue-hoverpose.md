

- SwiftUI
- PencilSqueezeGestureValue
-  hoverPose 

Instance Property

# hoverPose

The location and distance of an Apple Pencil hovering in the area above the view’s bounds when the squeeze gesture occurred.

iOS 17.5+iPadOS 17.5+Mac Catalyst 17.5+macOS 14.5+

``` source
let hoverPose: PencilHoverPose?
```

## Discussion

If the Apple Pencil was hovering in the area above the view’s bounds when the user squeezed their Apple Pencil, this property describes its pose relative to that view.

Conversely, if the Apple Pencil wasn’t hovering in the area above the view’s bounds or if the device can’t detect a hovering Apple Pencil, this property is `nil`.

