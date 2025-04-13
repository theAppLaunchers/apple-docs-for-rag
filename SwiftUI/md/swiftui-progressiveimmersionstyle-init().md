

- SwiftUI
- ProgressiveImmersionStyle
-  init() 

Initializer

# init()

An immersion style that displays unbounded content that partially replaces passthrough video.

visionOS 1.0+

``` source
init()
```

## Discussion

The system initially uses a radial portal effect that replaces passthrough in a portion of the field of view. People can interactively adjust the size of the portal by turning the Digital Crown, up to the point where the portal fully replaces passthrough. The latter matches the behavior of the full immersion style, including the configurable visibility of the viewer’s upper limbs.

When this immersion style is selected, the immersion amount reported by the closure of `View/onImmersionChange(_:)` is within the range of the immersion that this style is defined with.

Use the immersionStyle(selection:in:) scene modifier to specify this style for an ImmersiveSpace:

```
@main
struct ImmersiveApp: App {
    @State private var immersionStyle: ImmersionStyle = .progressive
    var body: some Scene {
        ImmersiveSpace { ... }
        .immersionStyle(selection: $immersionStyle, in: .progressive))
    }
}
```

The immersion style affects how windows interact with virtual objects in the environment. In `progressive` immersion, windows always render in front of virtual content, no matter how someone positions the window or the content. This helps people avoid losing track of windows behind virtual content when passthrough is off.

