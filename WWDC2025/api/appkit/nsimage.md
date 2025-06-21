*   [AppKit](/documentation/appkit)
*   NSImage

Class

# NSImage

A high-level interface for manipulating image data.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class NSImage
```
```
```
```
```
```
```
```

## [Overview](/documentation/AppKit/NSImage#overview)

You use instances of [`NSImage`](/documentation/appkit/nsimage) to load existing images, create new images, and draw the resulting image data into your views. Although you use this class predominantly for image-related operations, the class itself knows little about the underlying image data. Instead, it works in conjunction with one or more image representation objects (subclasses of [`NSImageRep`](/documentation/appkit/nsimagerep)) to manage and render the image data. For the most part, these interactions are transparent.

The class serves many purposes, providing support for the following tasks:

*   Loading images stored on disk or at a specified URL.
    
*   Drawing images into a view or graphics context.
    
*   Providing the contents of a [`CALayer`](/documentation/QuartzCore/CALayer) object.
    
*   Creating new images based on a series of captured drawing commands.
    
*   Producing versions of the image in a different format.
    

The `NSImage` class itself is capable of managing image data in a variety of formats. The specific list of formats is dependent on the version of the operating system but includes many standard formats such as TIFF, JPEG, GIF, PNG, and PDF among others. AppKit manages each format using a specific type of image representation object, whose job is to manage the actual image data. You can get a list of supported formats using the methods described in Determining Supported Types of Images.

For more information about how to use image objects in your app, see [Cocoa Drawing Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaDrawingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40003290).

### [Using Images with Core Animation Layers](/documentation/AppKit/NSImage#Using-Images-with-Core-Animation-Layers)

Although you can assign an `NSImage` object directly to the [`contents`](/documentation/QuartzCore/CALayer/contents) property of a [`CALayer`](/documentation/QuartzCore/CALayer) object, doing so may not always yield the best results. Instead of using your image object, you can use the [`layerContents(forContentsScale:)`](/documentation/appkit/nsimage/layercontents\(forcontentsscale:\)) method to obtain an object that you can use for your layer’s contents. The image created by that method serves as the contents of a layer, which also supports all of the layer’s gravity modes. By contrast, the `NSImage` class supports only the [`resize`](/documentation/QuartzCore/CALayerContentsGravity/resize), [`resizeAspect`](/documentation/QuartzCore/CALayerContentsGravity/resizeAspect), and [`resizeAspectFill`](/documentation/QuartzCore/CALayerContentsGravity/resizeAspectFill) modes.

Before calling the [`layerContents(forContentsScale:)`](/documentation/appkit/nsimage/layercontents\(forcontentsscale:\)) method, use the [`recommendedLayerContentsScale(_:)`](/documentation/appkit/nsimage/recommendedlayercontentsscale\(_:\)) method to get the recommended scale factor for the resulting image. The code listing below shows a typical example that uses the scale factor of a window’s backing store as the desired scale factor. From that scale factor, the code gets the scale factor for the specified image object and creates an object that you assign to the layer. You might use this code for images that fit the layer bounds precisely or for which you rely on the [`contentsGravity`](/documentation/QuartzCore/CALayer/contentsGravity) property of the layer to position or scale the image.

Listing 1. Assigning an image to a layer

```

```
static void updateLayerWithImageInWindow1(NSImage *image, CALayer *layer, NSWindow *window) {
   CGFloat desiredScaleFactor = [window backingScaleFactor];
   CGFloat actualScaleFactor = [image recommendedLayerContentsScale:desiredScaleFactor];
 
   id layerContents = [image layerContentsForContentsScale:actualScaleFactor];
 
   [layer setContents:layerContents];
   [layer setContentsScale:actualScaleFactor];
}
```

```

## [Topics](/documentation/AppKit/NSImage#topics)

### [Creating Images by Name](/documentation/AppKit/NSImage#Creating-Images-by-Name)

[

Configuring and displaying symbol images in your UI](/documentation/UIKit/configuring-and-displaying-symbol-images-in-your-ui)

Create scalable images that integrate with your app’s text, and adjust the appearance of those images dynamically.

[`init?(named: NSImage.Name)`](/documentation/appkit/nsimage/init\(named:\))

Returns the image object associated with the specified name.

[`convenience init?(systemSymbolName: String, accessibilityDescription: String?)`](/documentation/appkit/nsimage/init\(systemsymbolname:accessibilitydescription:\))

Creates a symbol image with the system symbol name and accessibility description you specify.

[`convenience init?(systemSymbolName: String, variableValue: Double, accessibilityDescription: String?)`](/documentation/appkit/nsimage/init\(systemsymbolname:variablevalue:accessibilitydescription:\))

Creates a symbol image with the system symbol name and variable value you specify.

[`convenience init?(symbolName: String, variableValue: Double)`](/documentation/appkit/nsimage/init\(symbolname:variablevalue:\))

Creates a symbol image with the symbol name and variable value you specify.

[`convenience init?(symbolName: String, bundle: Bundle?, variableValue: Double)`](/documentation/appkit/nsimage/init\(symbolname:bundle:variablevalue:\))

[`convenience init(resource: ImageResource)`](/documentation/appkit/nsimage/init\(resource:\))

```swift
```swift
```swift
func setName(NSImage.Name?) -> Bool
```
```

Registers the image object under the specified name.
```
```swift
```swift
```swift
func name() -> NSImage.Name?
```
```

Returns the name associated with the image, if any.
```
```swift
```swift
```swift
typealias Name
```
```

Named images, defined by the system or you, for use in your app.
```

[`convenience init(imageLiteralResourceName: String)`](/documentation/appkit/nsimage/init\(imageliteralresourcename:\))

Creates an image initialized with the specified resource name.

### [Creating Dynamically Drawn Images](/documentation/AppKit/NSImage#Creating-Dynamically-Drawn-Images)

[`convenience init(size: NSSize, flipped: Bool, drawingHandler: (NSRect) -> Bool)`](/documentation/appkit/nsimage/init\(size:flipped:drawinghandler:\))

Creates and returns an image object whose contents are drawn using the specified block.

### [Creating Images from Resource Files](/documentation/AppKit/NSImage#Creating-Images-from-Resource-Files)

[`convenience init?(byReferencingFile: String)`](/documentation/appkit/nsimage/init\(byreferencingfile:\))

Initializes and returns an image object using the specified file.

[`convenience init(byReferencing: URL)`](/documentation/appkit/nsimage/init\(byreferencing:\))

Initializes and returns an image object using the specified URL.

[`convenience init?(contentsOfFile: String)`](/documentation/appkit/nsimage/init\(contentsoffile:\))

Initializes and returns an image object with the contents of the specified file.

[`convenience init?(contentsOf: URL)`](/documentation/appkit/nsimage/init\(contentsof:\))

Initializes and returns an image object with the contents of the specified URL.

### [Creating Images from Existing Data](/documentation/AppKit/NSImage#Creating-Images-from-Existing-Data)

[`convenience init?(data: Data)`](/documentation/appkit/nsimage/init\(data:\))

Initializes and returns an image object using the provided image data.

[`convenience init?(dataIgnoringOrientation: Data)`](/documentation/appkit/nsimage/init\(dataignoringorientation:\))

Initializes and returns an image object using the provided image data and ignoring the EXIF orientation tags.

[`convenience init(cgImage: CGImage, size: NSSize)`](/documentation/appkit/nsimage/init\(cgimage:size:\))

Creates a new image using the contents of the provided image.

[`convenience init?(pasteboard: NSPasteboard)`](/documentation/appkit/nsimage/init\(pasteboard:\))

Initializes and returns an image object with data from the specified pasteboard.

[`init(coder: NSCoder)`](/documentation/appkit/nsimage/init\(coder:\))

Initializes and returns an image object from data in an unarchiver.

### [Creating Empty Images](/documentation/AppKit/NSImage#Creating-Empty-Images)

[`init(size: NSSize)`](/documentation/appkit/nsimage/init\(size:\))

Initializes and returns an image object with the specified dimensions.

### [Creating Symbol Images](/documentation/AppKit/NSImage#Creating-Symbol-Images)

```swift
```swift
```swift
```swift
func withSymbolConfiguration(NSImage.SymbolConfiguration) -> NSImage?
```
```

Creates a new symbol image with the specified configuration.
```
```swift
```swift
```swift
class SymbolConfiguration
```
```

An object that contains the specific font, style, and weight attributes to apply to a symbol image.
```
```

### [Getting the Symbol Image Configuration](/documentation/AppKit/NSImage#Getting-the-Symbol-Image-Configuration)

```swift
```swift
```swift
```swift
var symbolConfiguration: NSImage.SymbolConfiguration
```
```

The configuration details for a symbol image.
```
```

### [Managing Loading and Drawing of Images](/documentation/AppKit/NSImage#Managing-Loading-and-Drawing-of-Images)

```swift
```swift
```swift
```swift
var delegate: (any NSImageDelegate)?
```
```

The image’s delegate object.
```
```swift
```swift
```swift
protocol NSImageDelegate
```
```

A set of optional methods that you can use to respond to drawing failures and manage incremental loads.
```
```

### [Setting Attributes of Images](/documentation/AppKit/NSImage#Setting-Attributes-of-Images)

```swift
```swift
```swift
```swift
var size: NSSize
```
```

The size of the image.
```
```swift
```swift
```swift
var isTemplate: Bool
```
```

A Boolean value that determines whether the image represents a template image.
```
```swift
```swift
```swift
var isTemplate: Bool
```
```

A Boolean value that determines whether the image represents a template image.
```
```

### [Determining Supported Types of Images](/documentation/AppKit/NSImage#Determining-Supported-Types-of-Images)

```swift
```swift
```swift
```swift
class func canInit(with: NSPasteboard) -> Bool
```
```

Tests whether the image can create an instance of itself using pasteboard data.
```
```swift
```swift
```swift
class var imageTypes: [String]
```
```

Returns an array of UTI strings identifying the image types supported by the registered image representation objects, either directly or through a user-installed filter service.
```
```swift
```swift
```swift
class var imageUnfilteredTypes: [String]
```
```

Returns an array of UTI strings identifying the image types supported directly by the registered image representation objects.
```
```

### [Working with Representations of Images](/documentation/AppKit/NSImage#Working-with-Representations-of-Images)

```swift
```swift
```swift
```swift
func addRepresentation(NSImageRep)
```
```

Adds the specified image representation object to the image.
```
```swift
```swift
```swift
func addRepresentations([NSImageRep])
```
```

Adds an array of image representation objects to the image.
```
```swift
```swift
```swift
var representations: [NSImageRep]
```
```

An array containing all of the image object’s image representations.
```
```swift
```swift
```swift
func removeRepresentation(NSImageRep)
```
```

Removes and releases the specified image representation.
```
```swift
```swift
```swift
func bestRepresentation(for: NSRect, context: NSGraphicsContext?, hints: [NSImageRep.HintKey : Any]?) -> NSImageRep?
```
```

Returns the best representation of the image for the specified rectangle using the provided hints.
```
```swift
```swift
```swift
struct HintKey
```
```

Constants for the keys to include in a hints dictionary when drawing the image.
```
```swift
```swift
```swift
enum LayoutDirection
```
```

Constants that describe the layout direction for the image.
```
```

### [Setting the Representation Selection Criteria for Images](/documentation/AppKit/NSImage#Setting-the-Representation-Selection-Criteria-for-Images)

```swift
```swift
```swift
```swift
var prefersColorMatch: Bool
```
```

A Boolean value that indicates whether the image prefers to choose image representations using color-matching or resolution-matching.
```
```swift
```swift
```swift
var usesEPSOnResolutionMismatch: Bool
```
```

A Boolean value that indicates whether EPS representations are preferred when no other representations match the resolution of the device.
```
```swift
```swift
```swift
var matchesOnMultipleResolution: Bool
```
```

A Boolean value that indicates whether image representations whose resolution is an integral multiple of the device resolution are a match.
```
```

### [Drawing Images](/documentation/AppKit/NSImage#Drawing-Images)

```swift
```swift
```swift
```swift
func draw(in: NSRect)
```
```

Draws the image in the specified rectangle.
```
```swift
```swift
```swift
func draw(at: NSPoint, from: NSRect, operation: NSCompositingOperation, fraction: CGFloat)
```
```

Draws all or part of the image at the specified point in the current coordinate system.
```
```swift
```swift
```swift
func draw(in: NSRect, from: NSRect, operation: NSCompositingOperation, fraction: CGFloat)
```
```

Draws all or part of the image in the specified rectangle in the current coordinate system.
```
```swift
```swift
```swift
func draw(in: NSRect, from: NSRect, operation: NSCompositingOperation, fraction: CGFloat, respectFlipped: Bool, hints: [NSImageRep.HintKey : Any]?)
```
```

Draws all or part of the image in the specified rectangle respecting the hints and the orientation of the current coordinate system.
```
```swift
```swift
```swift
func drawRepresentation(NSImageRep, in: NSRect) -> Bool
```
```

Draws the image using the specified image representation object.
```
```swift
```swift
```swift
enum NSCompositingOperation
```
```

Constants that describe compositing operators in terms of source and destination images, each having an opaque and transparent region.
```
```

### [Managing Drawing Options](/documentation/AppKit/NSImage#Managing-Drawing-Options)

```swift
```swift
```swift
```swift
var isValid: Bool
```
```

A Boolean value that indicates whether it is possible to draw an image representation.
```
```swift
```swift
```swift
var backgroundColor: NSColor
```
```

The background color for the image.
```
```swift
```swift
```swift
var capInsets: NSEdgeInsets
```
```

The cap insets for the image.
```
```swift
```swift
```swift
var resizingMode: NSImage.ResizingMode
```
```

The resizing mode for the image.
```
```swift
```swift
```swift
enum ResizingMode
```
```

Constants that describe the resizing mode for the image.
```
```

### [Working with Alignment Metadata](/documentation/AppKit/NSImage#Working-with-Alignment-Metadata)

```swift
```swift
```swift
```swift
var alignmentRect: NSRect
```
```

A rectangle that you can use to position the image during layout.
```
```

### [Managing Caching Options](/documentation/AppKit/NSImage#Managing-Caching-Options)

```swift
```swift
```swift
```swift
var cacheMode: NSImage.CacheMode
```
```

The image’s caching mode.
```
```swift
```swift
```swift
func recache()
```
```

Invalidates and frees offscreen caches of all image representations.
```
```swift
```swift
```swift
enum CacheMode
```
```

Constants that specify the caching policy on a per-image basis.
```
```

### [Producing TIFF Data for Images](/documentation/AppKit/NSImage#Producing-TIFF-Data-for-Images)

```swift
```swift
```swift
```swift
var tiffRepresentation: Data?
```
```

A data object containing TIFF data for all of the image representations in the image.
```
```swift
```swift
```swift
func tiffRepresentation(using: NSBitmapImageRep.TIFFCompression, factor: Float) -> Data?
```
```

Returns a data object that contains TIFF data with the specified compression settings for all of the image representations in the image.
```
```

### [Producing Core Graphics Images](/documentation/AppKit/NSImage#Producing-Core-Graphics-Images)

```swift
```swift
```swift
```swift
func cgImage(forProposedRect: UnsafeMutablePointer<NSRect>?, context: NSGraphicsContext?, hints: [NSImageRep.HintKey : Any]?) -> CGImage?
```
```

Returns a Core Graphics image based on the contents of the current image object.
```
```

### [Hit-Testing Images](/documentation/AppKit/NSImage#Hit-Testing-Images)

```swift
```swift
```swift
```swift
func hitTest(NSRect, withDestinationRect: NSRect, context: NSGraphicsContext?, hints: [NSImageRep.HintKey : Any]?, flipped: Bool) -> Bool
```
```

Returns whether the destination rectangle would intersect a non-transparent portion of the image.
```
```

### [Managing Image Accessibility](/documentation/AppKit/NSImage#Managing-Image-Accessibility)

```swift
```swift
```swift
```swift
var accessibilityDescription: String?
```
```

The image’s accessibility description.
```
```

### [Using Images with Core Animation](/documentation/AppKit/NSImage#Using-Images-with-Core-Animation)

```swift
```swift
```swift
```swift
func layerContents(forContentsScale: CGFloat) -> Any
```
```

Returns an object that may be used as the contents of a layer.
```
```swift
```swift
```swift
func recommendedLayerContentsScale(CGFloat) -> CGFloat
```
```

Returns the recommended layer contents scale for this image.
```
```

### [Managing Axis Matching](/documentation/AppKit/NSImage#Managing-Axis-Matching)

```swift
```swift
```swift
```swift
var matchesOnlyOnBestFittingAxis: Bool
```
```

A Boolean value that indicates whether the image matches only on the best fitting axis.
```
```

### [Localizing Images](/documentation/AppKit/NSImage#Localizing-Images)

```swift
```swift
```swift
```swift
func withLocale(Locale?) -> NSImage
```
```
```
```swift
```swift
```swift
var locale: Locale?
```
```
```
```

### [Deprecated](/documentation/AppKit/NSImage#Deprecated)

[

API Reference

Deprecated Symbols](/documentation/appkit/nsimage-deprecated-symbols)

Review symbols that are no longer supported, and find the replacements to use instead.

### [Enumerations](/documentation/AppKit/NSImage#Enumerations)

```swift
```swift
```swift
```swift
enum DynamicRange
```
```

Describes how High Dynamic Range (HDR) image content displays.
```
```

## [Relationships](/documentation/AppKit/NSImage#relationships)

### [Inherits From](/documentation/AppKit/NSImage#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/AppKit/NSImage#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`Copyable`](/documentation/Swift/Copyable)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSCopying`](/documentation/Foundation/NSCopying)
*   [`NSItemProviderReading`](/documentation/Foundation/NSItemProviderReading)
*   [`NSItemProviderWriting`](/documentation/Foundation/NSItemProviderWriting)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSPasteboardReading`](/documentation/appkit/nspasteboardreading)
*   [`NSPasteboardWriting`](/documentation/appkit/nspasteboardwriting)
*   [`NSSecureCoding`](/documentation/Foundation/NSSecureCoding)
*   [`Transferable`](/documentation/CoreTransferable/Transferable)

## [See Also](/documentation/AppKit/NSImage#see-also)

### [Images](/documentation/AppKit/NSImage#Images)

[

Providing images for different appearances](/documentation/UIKit/providing-images-for-different-appearances)

Supply image resources appropriate for light and dark appearances and for high-contrast environments.

[

Supporting Continuity Camera in Your Mac App](/documentation/appkit/supporting-continuity-camera-in-your-mac-app)

Incorporate scanned documents and pictures from a user’s iPhone, iPad, or iPod touch into your Mac app using Continuity Camera.

[

Supporting HDR images in your app](/documentation/UIKit/supporting-hdr-images-in-your-app)

​ Load, display, edit, and save HDR images using SwiftUI and Core Image. ​

[

Applying Apple HDR effect to your photos](/documentation/appkit/applying-apple-hdr-effect-to-your-photos)

You can decode and apply Apple’s HDR gain map to your own images.

```swift
```swift
```swift
protocol NSImageDelegate
```
```

A set of optional methods that you can use to respond to drawing failures and manage incremental loads.
```
```swift
```swift
```swift
class NSImageRep
```
```

A semiabstract superclass that provides subclasses that you use to draw an image from a particular type of source data.
```