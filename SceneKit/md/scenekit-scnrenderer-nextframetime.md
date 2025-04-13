

- SceneKit
- SCNRenderer
-  nextFrameTime 

Instance Property

# nextFrameTime

The timestamp for the next frame to be rendered.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOS

``` source
var nextFrameTime: CFTimeInterval { get }
```

## Discussion

If the renderer’s scene has any attached actions or animations, use this property to determine how long your app should wait before telling the renderer to draw another frame. If this property’s value matches that of the renderer’s currentTime property, the scene contains a continuous animation—schedule your next render at whatever time best maintains your app’s performance. If the value is infinite, the scene has no running actions or animations.

