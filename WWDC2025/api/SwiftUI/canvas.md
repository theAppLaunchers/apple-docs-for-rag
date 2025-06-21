*   [SwiftUI](/documentation/swiftui)
*   Canvas

Structure

# Canvas

A view type that supports immediate mode drawing.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct Canvas<Symbols> where Symbols : [`View`](/documentation/swiftui/view)
```
```
```
```
```
```
```
```

## [Overview](/documentation/SwiftUI/Canvas#overview)

Use a canvas to draw rich and dynamic 2D graphics inside a SwiftUI view. The canvas passes a [`GraphicsContext`](/documentation/swiftui/graphicscontext) to the closure that you use to perform immediate mode drawing operations. The canvas also passes a [`CGSize`](/documentation/CoreFoundation/CGSize) value that you can use to customize what you draw. For example, you can use the context’s [`stroke(_:with:lineWidth:)`](/documentation/swiftui/graphicscontext/stroke\(_:with:linewidth:\)) command to draw a [`Path`](/documentation/swiftui/path) instance:

```

```
Canvas { context, size in
    context.stroke(
        Path(ellipseIn: CGRect(origin: .zero, size: size)),
        with: .color(.green),
        lineWidth: 4)
}
.frame(width: 300, height: 200)
.border(Color.blue)
```

```

The example above draws the outline of an ellipse that exactly inscribes a canvas with a blue border:

![A screenshot of a canvas view that shows the green outline of an](https://docs-assets.developer.apple.com/published/da33312de456cfbf0dfa4f0f517083c8/Canvas-1%402x.png)

In addition to outlined and filled paths, you can draw images, text, and complete SwiftUI views. To draw views, use the [`init(opaque:colorMode:rendersAsynchronously:renderer:symbols:)`](/documentation/swiftui/canvas/init\(opaque:colormode:rendersasynchronously:renderer:symbols:\)) method to supply views that you can reference from inside the renderer. You can also add masks, apply filters, perform transforms, control blending, and more. For information about how to draw, see [`GraphicsContext`](/documentation/swiftui/graphicscontext).

A canvas doesn’t offer interactivity or accessibility for individual elements, including for views that you pass in as symbols. However, it might provide better performance for a complex drawing that involves dynamic data. Use a canvas to improve performance for a drawing that doesn’t primarily involve text or require interactive elements.

## [Topics](/documentation/SwiftUI/Canvas#topics)

### [Creating a canvas](/documentation/SwiftUI/Canvas#Creating-a-canvas)

[`init(opaque: Bool, colorMode: ColorRenderingMode, rendersAsynchronously: Bool, renderer: (inout GraphicsContext, CGSize) -> Void)`](/documentation/swiftui/canvas/init\(opaque:colormode:rendersasynchronously:renderer:\))

Creates and configures a canvas.

[`init(opaque: Bool, colorMode: ColorRenderingMode, rendersAsynchronously: Bool, renderer: (inout GraphicsContext, CGSize) -> Void, symbols: () -> Symbols)`](/documentation/swiftui/canvas/init\(opaque:colormode:rendersasynchronously:renderer:symbols:\))

Creates and configures a canvas that you supply with renderable child views.

### [Managing opacity and color](/documentation/SwiftUI/Canvas#Managing-opacity-and-color)

```swift
```swift
```swift
```swift
var isOpaque: Bool
```
```

A Boolean that indicates whether the canvas is fully opaque.
```
```swift
```swift
```swift
var colorMode: ColorRenderingMode
```
```

The working color space and storage format of the canvas.
```
```

### [Referencing symbols](/documentation/SwiftUI/Canvas#Referencing-symbols)

```swift
```swift
```swift
```swift
var symbols: Symbols
```
```

A view that provides child views that you can use in the drawing callback.
```
```

### [Rendering](/documentation/SwiftUI/Canvas#Rendering)

```swift
```swift
```swift
```swift
var rendersAsynchronously: Bool
```
```

A Boolean that indicates whether the canvas can present its contents to its parent view asynchronously.
```
```swift
```swift
```swift
var renderer: (inout GraphicsContext, CGSize) -> Void
```
```

The drawing callback that you use to draw into the canvas.
```
```

## [Relationships](/documentation/SwiftUI/Canvas#relationships)

### [Conforms To](/documentation/SwiftUI/Canvas#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`View`](/documentation/swiftui/view)
    
    Conforms when `Symbols` conforms to `View`.
    

## [See Also](/documentation/SwiftUI/Canvas#see-also)

### [Immediate mode drawing](/documentation/SwiftUI/Canvas#Immediate-mode-drawing)

[

Add Rich Graphics to Your SwiftUI App](/documentation/swiftui/add_rich_graphics_to_your_swiftui_app)

Make your apps stand out by adding background materials, vibrancy, custom graphics, and animations.

```swift
```swift
```swift
struct GraphicsContext
```
```

An immediate mode drawing destination, and its current state.
```