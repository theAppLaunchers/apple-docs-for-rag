*   [SwiftUI](/documentation/swiftui)
*   Material

Structure

# Material

A background material type.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct Material
```
```
```
```
```
```
```
```

## [Overview](/documentation/SwiftUI/Material#overview)

You can apply a blur effect to a view that appears behind another view by adding a material with the [`background(_:ignoresSafeAreaEdges:)`](/documentation/swiftui/view/background\(_:ignoressafeareaedges:\)) modifier:

```

```
ZStack {
    Color.teal
    Label("Flag", systemImage: "flag.fill")
        .padding()
        .background(.regularMaterial)
}
```

```

In the example above, the [`ZStack`](/documentation/swiftui/zstack) layers a [`Label`](/documentation/swiftui/label) on top of the color [`teal`](/documentation/swiftui/shapestyle/teal). The background modifier inserts the regular material below the label, blurring the part of the background that the label — including its padding — covers:

![A screenshot of a label on a teal background, where the area behind](https://docs-assets.developer.apple.com/published/ec52cb3477c1a5d9010255e4b9a0471c/Material-1%402x.png)

A material isn’t a view, but adding a material is like inserting a translucent layer between the modified view and its background:

![An illustration that shows a background layer below a material layer,](https://docs-assets.developer.apple.com/published/ed7c89d0a28ecc2dc6fde740b26d8c16/Material-2%402x.png)

The blurring effect provided by the material isn’t simple opacity. Instead, it uses a platform-specific blending that produces an effect that resembles heavily frosted glass. You can see this more easily with a complex background, like an image:

```

```
ZStack {
    Image("chili_peppers")
        .resizable()
        .aspectRatio(contentMode: .fit)
    Label("Flag", systemImage: "flag.fill")
        .padding()
        .background(.regularMaterial)
}
```

```

![A screenshot of a label on an image background, where the area behind](https://docs-assets.developer.apple.com/published/258a1d722beb2f0f3fcea8da8e586d81/Material-3%402x.png)

For physical materials, the degree to which the background colors pass through depends on the thickness. The effect also varies with light and dark appearance:

![An array of labels on a teal background. The first column, labeled light](https://docs-assets.developer.apple.com/published/1968a1a6b1ac0e4648274c39838f0cfc/Material-4%402x.png)

If you need a material to have a particular shape, you can use the [`background(_:in:fillStyle:)`](/documentation/swiftui/view/background\(_:in:fillstyle:\)) modifier. For example, you can create a material with rounded corners:

```

```
ZStack {
    Color.teal
    Label("Flag", systemImage: "flag.fill")
        .padding()
        .background(.regularMaterial, in: RoundedRectangle(cornerRadius: 8))
}
```

```

![A screenshot of a label on a teal background, where the area behind](https://docs-assets.developer.apple.com/published/cc2fb03f54a0c65238963b18f70d2cfb/Material-5%402x.png)

When you add a material, foreground elements exhibit vibrancy, a context-specific blend of the foreground and background colors that improves contrast. However using [`foregroundStyle(_:)`](/documentation/swiftui/view/foregroundstyle\(_:\)) to set a custom foreground style — excluding the hierarchical styles, like [`secondary`](/documentation/swiftui/shapestyle/secondary-swift.type.property) — disables vibrancy.

Note

A material blurs a background that’s part of your app, but not what appears behind your app on the screen. For example, the content on the Home Screen doesn’t affect the appearance of a widget.

## [Topics](/documentation/SwiftUI/Material#topics)

### [Getting material types](/documentation/SwiftUI/Material#Getting-material-types)

[`static let ultraThin: Material`](/documentation/swiftui/material/ultrathin)

A mostly translucent material.

[`static let thin: Material`](/documentation/swiftui/material/thin)

A material that’s more translucent than opaque.

[`static let regular: Material`](/documentation/swiftui/material/regular)

A material that’s somewhat translucent.

[`static let thick: Material`](/documentation/swiftui/material/thick)

A material that’s more opaque than translucent.

[`static let ultraThick: Material`](/documentation/swiftui/material/ultrathick)

A mostly opaque material.

[`static let bar: Material`](/documentation/swiftui/material/bar)

A material matching the style of system toolbars.

### [Instance Methods](/documentation/SwiftUI/Material#Instance-Methods)

```swift
```swift
```swift
```swift
func materialActiveAppearance(MaterialActiveAppearance) -> Material
```
```

Sets an explicit active appearance for this material.
```
```

## [Relationships](/documentation/SwiftUI/Material#relationships)

### [Conforms To](/documentation/SwiftUI/Material#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`ShapeStyle`](/documentation/swiftui/shapestyle)

## [See Also](/documentation/SwiftUI/Material#see-also)

### [Supporting types](/documentation/SwiftUI/Material#Supporting-types)

```swift
```swift
```swift
```swift
struct AngularGradient
```
```

An angular gradient.
```
```swift
```swift
```swift
struct EllipticalGradient
```
```

A radial gradient that draws an ellipse.
```
```swift
```swift
```swift
struct LinearGradient
```
```

A linear gradient.
```
```swift
```swift
```swift
struct RadialGradient
```
```

A radial gradient.
```
```swift
```swift
```swift
struct ImagePaint
```
```

A shape style that fills a shape by repeating a region of an image.
```
```swift
```swift
```swift
struct HierarchicalShapeStyle
```
```

A shape style that maps to one of the numbered content styles.
```
```swift
```swift
```swift
struct HierarchicalShapeStyleModifier
```
```

Styles that you can apply to hierarchical shapes.
```
```swift
```swift
```swift
struct ForegroundStyle
```
```

The foreground style in the current context.
```
```swift
```swift
```swift
struct BackgroundStyle
```
```

The background style in the current context.
```
```swift
```swift
```swift
struct SelectionShapeStyle
```
```

A style used to visually indicate selection following platform conventional colors and behaviors.
```
```swift
```swift
```swift
struct SeparatorShapeStyle
```
```

A style appropriate for foreground separator or border lines.
```
```swift
```swift
```swift
struct TintShapeStyle
```
```

A style that reflects the current tint color.
```
```swift
```swift
```swift
struct FillShapeStyle
```
```

A shape style that displays one of the overlay fills.
```
```swift
```swift
```swift
struct LinkShapeStyle
```
```

A style appropriate for links.
```
```swift
```swift
```swift
struct PlaceholderTextShapeStyle
```
```

A style appropriate for placeholder text.
```
```