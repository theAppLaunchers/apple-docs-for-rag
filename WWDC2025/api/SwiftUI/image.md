*   [SwiftUI](/documentation/swiftui)
*   Image

Structure

# Image

A view that displays an image.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@frozen
struct Image
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/SwiftUI/Image#mentions)

[

Building layouts with stack views](/documentation/swiftui/building-layouts-with-stack-views)

[

Creating performant scrollable stacks](/documentation/swiftui/creating-performant-scrollable-stacks)

[

Configuring views](/documentation/swiftui/configuring-views)

[

Fitting images into available space](/documentation/swiftui/fitting-images-into-available-space)

[

Displaying data in lists](/documentation/swiftui/displaying-data-in-lists)

## [Overview](/documentation/SwiftUI/Image#overview)

Use an `Image` instance when you want to add images to your SwiftUI app. You can create images from many sources:

*   Image files in your app’s asset library or bundle. Supported types include PNG, JPEG, HEIC, and more.
    
*   Instances of platform-specific image types, like [`UIImage`](/documentation/UIKit/UIImage) and [`NSImage`](/documentation/AppKit/NSImage).
    
*   A bitmap stored in a Core Graphics [`CGImage`](/documentation/CoreGraphics/CGImage) instance.
    
*   System graphics from the SF Symbols set.
    

The following example shows how to load an image from the app’s asset library or bundle and scale it to fit within its container:

```

```
Image("Landscape_4")
    .resizable()
    .aspectRatio(contentMode: .fit)
Text("Water wheel")
```

```

![An image of a water wheel and its adjoining building, resized to fit the](https://docs-assets.developer.apple.com/published/5d218460da75fc53e2a4398f3ab30a3b/Image-1%402x.png)

You can use methods on the `Image` type as well as standard view modifiers to adjust the size of the image to fit your app’s interface. Here, the `Image` type’s [`resizable(capInsets:resizingMode:)`](/documentation/swiftui/image/resizable\(capinsets:resizingmode:\)) method scales the image to fit the current view. Then, the [`aspectRatio(_:contentMode:)`](/documentation/swiftui/view/aspectratio\(_:contentmode:\)) view modifier adjusts this resizing behavior to maintain the image’s original aspect ratio, rather than scaling the x- and y-axes independently to fill all four sides of the view. The article [Fitting images into available space](/documentation/swiftui/fitting-images-into-available-space) shows how to apply scaling, clipping, and tiling to `Image` instances of different sizes.

An `Image` is a late-binding token; the system resolves its actual value only when it’s about to use the image in an environment.

### [Making images accessible](/documentation/SwiftUI/Image#Making-images-accessible)

To use an image as a control, use one of the initializers that takes a `label` parameter. This allows the system’s accessibility frameworks to use the label as the name of the control for users who use features like VoiceOver. For images that are only present for aesthetic reasons, use an initializer with the `decorative` parameter; the accessibility systems ignore these images.

## [Topics](/documentation/SwiftUI/Image#topics)

### [Creating an image](/documentation/SwiftUI/Image#Creating-an-image)

[`init(String, bundle: Bundle?)`](/documentation/swiftui/image/init\(_:bundle:\))

Creates a labeled image that you can use as content for controls.

[`init(String, variableValue: Double?, bundle: Bundle?)`](/documentation/swiftui/image/init\(_:variablevalue:bundle:\))

Creates a labeled image that you can use as content for controls, with a variable value.

[`init(ImageResource)`](/documentation/swiftui/image/init\(_:\))

Initialize an `Image` with an image resource.

### [Creating an image for use as a control](/documentation/SwiftUI/Image#Creating-an-image-for-use-as-a-control)

[`init(String, bundle: Bundle?, label: Text)`](/documentation/swiftui/image/init\(_:bundle:label:\))

Creates a labeled image that you can use as content for controls, with the specified label.

[`init(String, variableValue: Double?, bundle: Bundle?, label: Text)`](/documentation/swiftui/image/init\(_:variablevalue:bundle:label:\))

Creates a labeled image that you can use as content for controls, with the specified label and variable value.

[`init(CGImage, scale: CGFloat, orientation: Image.Orientation, label: Text)`](/documentation/swiftui/image/init\(_:scale:orientation:label:\))

Creates a labeled image based on a Core Graphics image instance, usable as content for controls.

### [Creating an image for decorative use](/documentation/SwiftUI/Image#Creating-an-image-for-decorative-use)

[`init(decorative: String, bundle: Bundle?)`](/documentation/swiftui/image/init\(decorative:bundle:\))

Creates an unlabeled, decorative image.

[`init(decorative: String, variableValue: Double?, bundle: Bundle?)`](/documentation/swiftui/image/init\(decorative:variablevalue:bundle:\))

Creates an unlabeled, decorative image, with a variable value.

[`init(decorative: CGImage, scale: CGFloat, orientation: Image.Orientation)`](/documentation/swiftui/image/init\(decorative:scale:orientation:\))

Creates an unlabeled, decorative image based on a Core Graphics image instance.

### [Creating a system symbol image](/documentation/SwiftUI/Image#Creating-a-system-symbol-image)

[`init(systemName: String)`](/documentation/swiftui/image/init\(systemname:\))

Creates a system symbol image.

[`init(systemName: String, variableValue: Double?)`](/documentation/swiftui/image/init\(systemname:variablevalue:\))

Creates a system symbol image with a variable value.

### [Creating an image from another image](/documentation/SwiftUI/Image#Creating-an-image-from-another-image)

[`init(uiImage: UIImage)`](/documentation/swiftui/image/init\(uiimage:\))

Creates a SwiftUI image from a UIKit image instance.

[`init(nsImage: NSImage)`](/documentation/swiftui/image/init\(nsimage:\))

Creates a SwiftUI image from an AppKit image instance.

### [Creating an image from drawing instructions](/documentation/SwiftUI/Image#Creating-an-image-from-drawing-instructions)

[`init(size: CGSize, label: Text?, opaque: Bool, colorMode: ColorRenderingMode, renderer: (inout GraphicsContext) -> Void)`](/documentation/swiftui/image/init\(size:label:opaque:colormode:renderer:\))

Initializes an image of the given size, with contents provided by a custom rendering closure.

### [Resizing images](/documentation/SwiftUI/Image#Resizing-images)

```swift
```swift
```swift
```swift
func resizable(capInsets: EdgeInsets, resizingMode: Image.ResizingMode) -> Image
```
```

Sets the mode by which SwiftUI resizes an image to fit its space.
```
```

### [Specifying rendering behavior](/documentation/SwiftUI/Image#Specifying-rendering-behavior)

```swift
```swift
```swift
```swift
func antialiased(Bool) -> Image
```
```

Specifies whether SwiftUI applies antialiasing when rendering the image.
```
```swift
```swift
```swift
func symbolRenderingMode(SymbolRenderingMode?) -> Image
```
```

Sets the rendering mode for symbol images within this view.
```
```swift
```swift
```swift
func renderingMode(Image.TemplateRenderingMode?) -> Image
```
```

Indicates whether SwiftUI renders an image as-is, or by using a different mode.
```
```swift
```swift
```swift
func interpolation(Image.Interpolation) -> Image
```
```

Specifies the current level of quality for rendering an image that requires interpolation.
```
```swift
```swift
```swift
enum TemplateRenderingMode
```
```

A type that indicates how SwiftUI renders images.
```
```swift
```swift
```swift
enum Interpolation
```
```

The level of quality for rendering an image that requires interpolation, such as a scaled image.
```
```

### [Specifying dynamic range](/documentation/SwiftUI/Image#Specifying-dynamic-range)

```swift
```swift
```swift
```swift
func allowedDynamicRange(Image.DynamicRange?) -> Image
```
```

Returns a new image configured with the specified allowed dynamic range.
```
```swift
```swift
```swift
var allowedDynamicRange: Image.DynamicRange?
```
```

The allowed dynamic range for the view, or nil.
```
```swift
```swift
```swift
struct DynamicRange
```
```
```
```

### [Instance Methods](/documentation/SwiftUI/Image#Instance-Methods)

```swift
```swift
```swift
```swift
func symbolColorRenderingMode(SymbolColorRenderingMode?) -> Image
```
```

Sets the color rendering mode of the image.

Beta
```
```swift
```swift
```swift
func symbolVariableValueMode(SymbolVariableValueMode?) -> Image
```
```

Sets the variable value mode mode for symbol images within this view.

Beta
```
```swift
```swift
```swift
func widgetAccentedRenderingMode(WidgetAccentedRenderingMode?) -> some View
```
```

Specifies the how to render an `Image` when using the `WidgetKit/WidgetRenderingMode/accented` mode.
```
```

### [Enumerations](/documentation/SwiftUI/Image#Enumerations)

```swift
```swift
```swift
```swift
enum Orientation
```
```

The orientation of an image.
```
```swift
```swift
```swift
enum ResizingMode
```
```

The modes that SwiftUI uses to resize an image to fit within its containing view.
```
```swift
```swift
```swift
enum Scale
```
```

A scale to apply to vector images relative to text.
```
```

### [Default Implementations](/documentation/SwiftUI/Image#Default-Implementations)

[

API Reference

Equatable Implementations](/documentation/swiftui/image/equatable-implementations)

## [Relationships](/documentation/SwiftUI/Image#relationships)

### [Conforms To](/documentation/SwiftUI/Image#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`JournalingSuggestionAsset`](/documentation/JournalingSuggestions/JournalingSuggestionAsset)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`Transferable`](/documentation/CoreTransferable/Transferable)
*   [`View`](/documentation/swiftui/view)