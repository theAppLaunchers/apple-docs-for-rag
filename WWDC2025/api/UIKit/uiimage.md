*   [UIKit](/documentation/uikit)
*   UIImage

Class

# UIImage

An object that manages image data in your app.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+watchOS 2.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class UIImage
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/UIKit/UIImage#mentions)

[

Understanding a drag item as a promise](/documentation/uikit/understanding-a-drag-item-as-a-promise)

[

Configuring and displaying symbol images in your UI](/documentation/uikit/configuring-and-displaying-symbol-images-in-your-ui)

[

Making a view into a drop destination](/documentation/uikit/making-a-view-into-a-drop-destination)

## [Overview](/documentation/UIKit/UIImage#overview)

You use image objects to represent image data of all kinds, and the [`UIImage`](/documentation/uikit/uiimage) class is capable of managing data for all image formats supported by the underlying platform. Image objects are immutable, so you always create them from existing image data, such as an image file on disk or programmatically created image data. An image object may contain a single image or a sequence of images for use in an animation.

You can use image objects in several different ways:

*   Assign an image to a [`UIImageView`](/documentation/uikit/uiimageview) object to display the image in your interface.
    
*   Use an image to customize system controls such as buttons, sliders, and segmented controls.
    
*   Draw an image directly into a view or other graphics context.
    
*   Pass an image to other APIs that might require image data.
    

Although image objects support all platform-native image formats, it’s recommended that you use PNG or JPEG files for most images in your app. Image objects are optimized for reading and displaying both formats, and those formats offer better performance than most other image formats. Because the PNG format is lossless, it’s especially recommended for the images you use in your app’s interface.

### [Create image objects](/documentation/UIKit/UIImage#Create-image-objects)

When creating image objects using the methods of this class, you must have existing image data located in a file or data structure. You can’t create an empty image and draw content into it. There are many options for creating image objects, each of which is best for specific situations:

*   Use the [`init(named:in:compatibleWith:)`](/documentation/uikit/uiimage/init\(named:in:compatiblewith:\)) method (or the [`init(named:)`](/documentation/uikit/uiimage/init\(named:\)) method) to create an image from an image asset or image file located in your app’s main bundle (or some other known bundle). Because these methods cache the image data automatically, they’re especially recommended for images that you use frequently.
    
*   Use the [`imageWithContentsOfFile:`](/documentation/uikit/uiimage/imagewithcontentsoffile:) or [`init(contentsOfFile:)`](/documentation/uikit/uiimage/init\(contentsoffile:\)) method to create an image object where the initial data isn’t in a bundle. These methods load the image data from disk each time, so don’t use them to load the same image repeatedly.
    
*   Use the [`animatedImage(with:duration:)`](/documentation/uikit/uiimage/animatedimage\(with:duration:\)) and [`animatedImageNamed(_:duration:)`](/documentation/uikit/uiimage/animatedimagenamed\(_:duration:\)) methods to create a single [`UIImage`](/documentation/uikit/uiimage) object comprised of multiple sequential images. Install the resulting image in a [`UIImageView`](/documentation/uikit/uiimageview) object to create animations in your interface.
    

Other methods of the [`UIImage`](/documentation/uikit/uiimage) class let you create animations from specific types of data, such as Core Graphics images or image data you create yourself. UIKit also provides the [`UIGraphicsGetImageFromCurrentImageContext()`](/documentation/uikit/uigraphicsgetimagefromcurrentimagecontext\(\)) function to create images from content you draw yourself. You use that function in conjunction with a bitmap-based graphics context, which you use to capture your drawing commands.

Note

Because image objects are immutable, you can’t change their properties after creation. Most image properties are set automatically using metadata in the accompanying image file or image data. The immutable nature of image objects also means they’re safe to create and use from any thread.

Image assets are the easiest way to manage the images that ship with your app. Each new Xcode project contains an assets library, to which you can add multiple image sets. An image set contains the variations of a single image that your app uses. A single image set can provide different versions of an image for different platforms, for different trait environments (compact or regular), and for different scale factors.

In addition to loading images from disk, you can ask the user to supply images from an available camera or photo library using a [`UIImagePickerController`](/documentation/uikit/uiimagepickercontroller) object. An image picker displays a custom user interface for selecting images. Accessing user-supplied images requires explicit user permission. For more information about using an image picker, see [`UIImagePickerController`](/documentation/uikit/uiimagepickercontroller).

### [Define a stretchable image](/documentation/UIKit/UIImage#Define-a-stretchable-image)

A stretchable image is one that defines regions where you can duplicate the underlying image data in an aesthetically pleasing way. Stretchable images are commonly used to create backgrounds that can grow or shrink to fill the available space.

Define a stretchable image by adding insets to an existing image using the [`resizableImage(withCapInsets:)`](/documentation/uikit/uiimage/resizableimage\(withcapinsets:\)) or [`resizableImage(withCapInsets:resizingMode:)`](/documentation/uikit/uiimage/resizableimage\(withcapinsets:resizingmode:\)) method. The insets subdivide the image into two or more parts. Specifying nonzero values for each inset yields an image divided into nine parts, as shown in the following image:

![An image that depicts how to use insets to define stretchable regions. The image on the left is stretched and shows Left, Right, Top, and Bottom insets. The image on the right is condensed and also shows Left, Right, Top, and Bottom insets.](https://docs-assets.developer.apple.com/published/a24122a4b3a9289007f9bcad22d8667d/media-1965929%402x.png)

Each inset defines the portion of the image that doesn’t stretch in the given dimension. The regions inside an image’s top and bottom insets maintain a fixed height, and the areas inside the left and right insets maintain a fixed width. The following image shows how each part of a nine-part image stretches as the image itself is stretched to fill the available space. The corners of the image don’t change size because they’re inside both a horizontal and vertical inset:

![An image that depicts the stretchable portions of a nine-part image. The image on the left is stretched. The image on the right is condensed. The corners of both images remain the same size.](https://docs-assets.developer.apple.com/published/dcf9ad7415ffdb2dd9a753a3be251cce/media-1965930%402x.png)

### [Compare images](/documentation/UIKit/UIImage#Compare-images)

The [`isEqual(_:)`](/documentation/ObjectiveC/NSObjectProtocol/isEqual\(_:\)) method is the only reliable way to determine whether two image objects contain the same image data. The following code illustrates the correct and incorrect ways to compare images.

```swift

```swift
// Load the same image twice.
```swift
```swift
let image1 = UIImage(named: "MyImage")
```
```
```swift
```swift
let image2 = UIImage(named: "MyImage")
```
```
 
// The image objects may be different, but the contents are still equal.
if image1 != nil && image1!.isEqual(image2) {
    // Correct. This technique compares the image data correctly.
} 
if image1 == image2 {
    // Incorrect! Direct object comparisons may not work.
}
```

```

```

```
// Load the same image twice.
UIImage* image1 = [UIImage imageNamed:@"MyImage"];
UIImage* image2 = [UIImage imageNamed:@"MyImage"];
 
// The image objects may be different, but the contents are still equal
if ([image1 isEqual:image2]) {
   // Correct. This technique compares the image data correctly.
}
 
if (image1 == image2) {
   // Incorrect! Direct object comparisons may not work.
}
```

```

### [Access the image data](/documentation/UIKit/UIImage#Access-the-image-data)

Image objects don’t provide direct access to their underlying image data. However, you can retrieve the image data in other formats for use in your app. Specifically, you can use the [`cgImage`](/documentation/uikit/uiimage/cgimage) and [`ciImage`](/documentation/uikit/uiimage/ciimage) properties to retrieve versions of the image that are compatible with Core Graphics and Core Image, respectively. You can also use the [`pngData()`](/documentation/uikit/uiimage/pngdata\(\)) and [`jpegData(compressionQuality:)`](/documentation/uikit/uiimage/jpegdata\(compressionquality:\)) functions to generate an [`NSData`](/documentation/Foundation/NSData) object containing the image data in either the PNG or JPEG format.

## [Topics](/documentation/UIKit/UIImage#topics)

### [Loading and caching images](/documentation/UIKit/UIImage#Loading-and-caching-images)

[

Providing images for different appearances](/documentation/uikit/providing-images-for-different-appearances)

Supply image resources appropriate for light and dark appearances and for high-contrast environments.

[

Configuring and displaying symbol images in your UI](/documentation/uikit/configuring-and-displaying-symbol-images-in-your-ui)

Create scalable images that integrate with your app’s text, and adjust the appearance of those images dynamically.

[

Creating custom symbol images for your app](/documentation/uikit/creating-custom-symbol-images-for-your-app)

Create, organize, and annotate symbol images using SF Symbols.

[`init?(named: String, in: Bundle?, compatibleWith: UITraitCollection?)`](/documentation/uikit/uiimage/init\(named:in:compatiblewith:\))

Creates an image object using the named image asset that’s compatible with the specified trait collection.

[`init?(named: String, in: Bundle?, with: UIImage.Configuration?)`](/documentation/uikit/uiimage/init\(named:in:with:\))

Creates an image by using the named image asset that’s compatible with the configuration you specify.

[`convenience init?(named: String, in: Bundle?, variableValue: Double, configuration: UIImage.Configuration?)`](/documentation/uikit/uiimage/init\(named:in:variablevalue:configuration:\))

Creates an image by using the name, configuration, and variable value you specify.

[`init?(named: String)`](/documentation/uikit/uiimage/init\(named:\))

Creates an image object from the specified named asset.

[`convenience init(imageLiteralResourceName: String)`](/documentation/uikit/uiimage/init\(imageliteralresourcename:\))

Returns the image object for the specified resource.

[`init?(systemName: String, withConfiguration: UIImage.Configuration?)`](/documentation/uikit/uiimage/init\(systemname:withconfiguration:\))

Creates an image object that contains a system symbol image with the specified configuration.

[`convenience init?(systemName: String, variableValue: Double, configuration: UIImage.Configuration?)`](/documentation/uikit/uiimage/init\(systemname:variablevalue:configuration:\))

Creates an image object that contains a system symbol image with the configuration and variable value you specify.

[`init?(systemName: String, compatibleWith: UITraitCollection?)`](/documentation/uikit/uiimage/init\(systemname:compatiblewith:\))

Creates an image object that contains a system symbol image appropriate for the specified traits.

[`init?(systemName: String)`](/documentation/uikit/uiimage/init\(systemname:\))

Creates an image object that contains a system symbol image.

[`convenience init(resource: ImageResource)`](/documentation/uikit/uiimage/init\(resource:\))

[

Building high-performance lists and collection views](/documentation/uikit/building-high-performance-lists-and-collection-views)

Improve the performance of lists and collections in your app with prefetching and image preparation.

### [Loading images for display](/documentation/UIKit/UIImage#Loading-images-for-display)

```swift
```swift
```swift
```swift
func preparingForDisplay() -> UIImage?
```
```

Decodes an image synchronously and provides a new one for display in views and animations.
```
```swift
```swift
```swift
func prepareForDisplay(completionHandler: (UIImage?) -> Void)
```
```

Decodes an image asynchronously and provides a new one for display in views and animations.
```
```swift
```swift
```swift
func preparingThumbnail(of: CGSize) -> UIImage?
```
```

Returns a new thumbnail image at the specified size.
```
```swift
```swift
```swift
func prepareThumbnail(of: CGSize, completionHandler: (UIImage?) -> Void)
```
```

Creates a thumbnail image at the specified size asynchronously on a background thread.
```
```

### [Creating and initializing image objects](/documentation/UIKit/UIImage#Creating-and-initializing-image-objects)

[`init?(contentsOfFile: String)`](/documentation/uikit/uiimage/init\(contentsoffile:\))

Initializes and returns the image object with the contents of the specified file.

[`init?(data: Data)`](/documentation/uikit/uiimage/init\(data:\))

Initializes and returns the image object with the specified data.

[`init?(data: Data, scale: CGFloat)`](/documentation/uikit/uiimage/init\(data:scale:\))

Initializes and returns the image object with the specified data and scale factor.

[`init(cgImage: CGImage)`](/documentation/uikit/uiimage/init\(cgimage:\))

Initializes and returns the image object with the specified Quartz image reference.

[`init(cgImage: CGImage, scale: CGFloat, orientation: UIImage.Orientation)`](/documentation/uikit/uiimage/init\(cgimage:scale:orientation:\))

Initializes and returns an image object with the specified scale and orientation factors.

[`init(ciImage: CIImage)`](/documentation/uikit/uiimage/init\(ciimage:\))

Initializes and returns an image object with the specified Core Image object.

[`init(ciImage: CIImage, scale: CGFloat, orientation: UIImage.Orientation)`](/documentation/uikit/uiimage/init\(ciimage:scale:orientation:\))

Initializes and returns an image object with the specified Core Image object and properties.

```swift
```swift
```swift
struct UIImageReader
```
```
```

### [Creating animated images](/documentation/UIKit/UIImage#Creating-animated-images)

```swift
```swift
```swift
```swift
class func animatedImageNamed(String, duration: TimeInterval) -> UIImage?
```
```

Creates and returns an animated image.
```
```swift
```swift
```swift
class func animatedImage(with: [UIImage], duration: TimeInterval) -> UIImage?
```
```

Creates and returns an animated image from an existing set of images.
```
```swift
```swift
```swift
class func animatedResizableImageNamed(String, capInsets: UIEdgeInsets, duration: TimeInterval) -> UIImage?
```
```

Creates and returns an animated image with end caps.
```
```swift
```swift
```swift
class func animatedResizableImageNamed(String, capInsets: UIEdgeInsets, resizingMode: UIImage.ResizingMode, duration: TimeInterval) -> UIImage?
```
```

Creates and returns an animated image with end caps and a specific resizing mode.
```
```

### [Changing the image attributes](/documentation/UIKit/UIImage#Changing-the-image-attributes)

```swift
```swift
```swift
```swift
func withConfiguration(UIImage.Configuration) -> UIImage
```
```

Returns a new version of the current image, replacing the current configuration attributes with the specified attributes.
```
```swift
```swift
```swift
func applyingSymbolConfiguration(UIImage.SymbolConfiguration) -> UIImage?
```
```

Returns a new version of the current image, applying the specified configuration attributes on top of the current attributes.
```
```swift
```swift
```swift
func imageFlippedForRightToLeftLayoutDirection() -> UIImage
```
```

Returns a new version of the current image that flips horizontally when it’s in a right-to-left layout.
```
```swift
```swift
```swift
func withHorizontallyFlippedOrientation() -> UIImage
```
```

Returns a new version of the image that’s a mirror of the original image.
```
```swift
```swift
```swift
func withRenderingMode(UIImage.RenderingMode) -> UIImage
```
```

Returns a new version of the image that uses the specified rendering mode.
```
```swift
```swift
```swift
func withAlignmentRectInsets(UIEdgeInsets) -> UIImage
```
```

Returns a new version of the image that uses the specified alignment insets.
```
```swift
```swift
```swift
func resizableImage(withCapInsets: UIEdgeInsets) -> UIImage
```
```

Returns a new version of the image with the specified cap insets.
```
```swift
```swift
```swift
func resizableImage(withCapInsets: UIEdgeInsets, resizingMode: UIImage.ResizingMode) -> UIImage
```
```

Returns a new version of the image with the specified cap insets and options.
```
```swift
```swift
```swift
func imageWithoutBaseline() -> UIImage
```
```

Creates a copy of the current image object without any baseline information.
```
```swift
```swift
```swift
func withBaselineOffset(fromBottom: CGFloat) -> UIImage
```
```

Creates a new image with a baseline at the specified offset from the bottom of the image.
```
```swift
```swift
```swift
class Configuration
```
```

A configuration object that contains the traits that the system uses when selecting the current image variant.
```
```swift
```swift
```swift
class SymbolConfiguration
```
```

An object that contains the specific font, size, style, and weight attributes to apply to a symbol image.
```
```

### [Getting standard system images](/documentation/UIKit/UIImage#Getting-standard-system-images)

```swift
```swift
```swift
```swift
class var add: UIImage
```
```

The standard image for indicating the addition of content.
```
```swift
```swift
```swift
class var remove: UIImage
```
```

The standard image for indicating the removal of content.
```
```swift
```swift
```swift
class var actions: UIImage
```
```

The standard image for indicating user-initiated actions.
```
```swift
```swift
```swift
class var checkmark: UIImage
```
```

The standard image for a checkmark on a filled-circle background.
```
```swift
```swift
```swift
class var strokedCheckmark: UIImage
```
```

The standard image for a checkmark on a tinted circle with a white-stroked border.
```
```

### [Getting the image data](/documentation/UIKit/UIImage#Getting-the-image-data)

```swift
```swift
```swift
```swift
var cgImage: CGImage?
```
```

The underlying Quartz image data.
```
```swift
```swift
```swift
var ciImage: CIImage?
```
```

The underlying Core Image data.
```
```swift
```swift
```swift
var images: [UIImage]?
```
```

The complete array of image objects that compose the animation of an animated object.
```
```swift
```swift
```swift
var imageAsset: UIImageAsset?
```
```

The image asset (if any) for the image.
```
```

### [Getting the image size and scale](/documentation/UIKit/UIImage#Getting-the-image-size-and-scale)

```swift
```swift
```swift
```swift
var scale: CGFloat
```
```

The scale factor of the image.
```
```swift
```swift
```swift
var size: CGSize
```
```

The logical dimensions, in points, for the image.
```
```

### [Accessing image attributes](/documentation/UIKit/UIImage#Accessing-image-attributes)

```swift
```swift
```swift
```swift
var imageOrientation: UIImage.Orientation
```
```

The orientation of the receiver’s image.
```
```swift
```swift
```swift
enum Orientation
```
```

Constants that specify the intended display orientation for an image.
```
```swift
```swift
```swift
var flipsForRightToLeftLayoutDirection: Bool
```
```

A Boolean value that indicates whether the image flips in a right-to-left layout.
```
```swift
```swift
```swift
var resizingMode: UIImage.ResizingMode
```
```

The resizing mode of the image.
```
```swift
```swift
```swift
enum ResizingMode
```
```

Constants that specify the possible resizing modes for an image.
```
```swift
```swift
```swift
var duration: TimeInterval
```
```

The time interval for displaying an animated image.
```
```swift
```swift
```swift
var capInsets: UIEdgeInsets
```
```

The end-cap insets.
```
```swift
```swift
```swift
var alignmentRectInsets: UIEdgeInsets
```
```

The alignment metadata for positioning the image during layout.
```
```swift
```swift
```swift
var isSymbolImage: Bool
```
```

A Boolean value that indicates whether the image is a symbol.
```
```

### [Getting the image configuration](/documentation/UIKit/UIImage#Getting-the-image-configuration)

```swift
```swift
```swift
```swift
var configuration: UIImage.Configuration?
```
```

The configuration details for the image.
```
```swift
```swift
```swift
var symbolConfiguration: UIImage.SymbolConfiguration?
```
```

The configuration details for a symbol image.
```
```swift
```swift
```swift
var traitCollection: UITraitCollection
```
```

The trait collection that describes the current variant of the image.
```
```

### [Specifying the dynamic range](/documentation/UIKit/UIImage#Specifying-the-dynamic-range)

```swift
```swift
```swift
```swift
var isHighDynamicRange: Bool
```
```
```
```swift
```swift
```swift
func imageRestrictedToStandardDynamicRange() -> UIImage
```
```
```
```swift
```swift
```swift
func heicData() -> Data?
```
```
```
```swift
```swift
```swift
enum DynamicRange
```
```
```
```

### [Managing the baseline](/documentation/UIKit/UIImage#Managing-the-baseline)

```swift
```swift
```swift
```swift
var baselineOffsetFromBottom: CGFloat?
```
```

The position of the baseline relative to the bottom of the image.
```
```

### [Getting rendering information](/documentation/UIKit/UIImage#Getting-rendering-information)

```swift
```swift
```swift
```swift
var renderingMode: UIImage.RenderingMode
```
```

A setting that determines how the app renders an image.
```
```swift
```swift
```swift
enum RenderingMode
```
```

Constants that specify the possible rendering modes for an image.
```
```swift
```swift
```swift
var imageRendererFormat: UIGraphicsImageRendererFormat
```
```

The preferred image renderer format for the image.
```
```

### [Tinting the image](/documentation/UIKit/UIImage#Tinting-the-image)

```swift
```swift
```swift
```swift
func withTintColor(UIColor) -> UIImage
```
```

Returns a new version of the current image with the specified tint color.
```
```swift
```swift
```swift
func withTintColor(UIColor, renderingMode: UIImage.RenderingMode) -> UIImage
```
```

Returns a new version of the image with a tint color that uses the specified rendering mode.
```
```

### [Drawing images](/documentation/UIKit/UIImage#Drawing-images)

```swift
```swift
```swift
```swift
func draw(at: CGPoint)
```
```

Draws the image at the specified point in the current context.
```
```swift
```swift
```swift
func draw(at: CGPoint, blendMode: CGBlendMode, alpha: CGFloat)
```
```

Draws the entire image at the specified point using the custom compositing options.
```
```swift
```swift
```swift
func draw(in: CGRect)
```
```

Draws the entire image in the specified rectangle, scaling it as necessary to fit.
```
```swift
```swift
```swift
func draw(in: CGRect, blendMode: CGBlendMode, alpha: CGFloat)
```
```

Draws the entire image in the specified rectangle using the specified compositing options.
```
```swift
```swift
```swift
func drawAsPattern(in: CGRect)
```
```

Draws a tiled Quartz pattern using the receiver’s contents as the tile pattern.
```
```

### [Exporting standard bitmap formats](/documentation/UIKit/UIImage#Exporting-standard-bitmap-formats)

```swift
```swift
```swift
```swift
func jpegData(compressionQuality: CGFloat) -> Data?
```
```

Returns a data object that contains the image in JPEG format.
```
```swift
```swift
```swift
func pngData() -> Data?
```
```

Returns a data object that contains the specified image in PNG format.
```
```

### [Deprecated](/documentation/UIKit/UIImage#Deprecated)

```swift
```swift
```swift
```swift
func stretchableImage(withLeftCapWidth: Int, topCapHeight: Int) -> UIImage
```
```

Creates and returns a new image object with the specified cap values.

Deprecated
```
```swift
```swift
```swift
var leftCapWidth: Int
```
```

The horizontal end-cap size.

Deprecated
```
```swift
```swift
```swift
var topCapHeight: Int
```
```

The vertical end-cap size.

Deprecated
```
```

## [Relationships](/documentation/UIKit/UIImage#relationships)

### [Inherits From](/documentation/UIKit/UIImage#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/UIKit/UIImage#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`Copyable`](/documentation/Swift/Copyable)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`JournalingSuggestionAsset`](/documentation/JournalingSuggestions/JournalingSuggestionAsset)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSItemProviderReading`](/documentation/Foundation/NSItemProviderReading)
*   [`NSItemProviderWriting`](/documentation/Foundation/NSItemProviderWriting)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSSecureCoding`](/documentation/Foundation/NSSecureCoding)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`UIAccessibilityIdentification`](/documentation/uikit/uiaccessibilityidentification)
*   [`UIItemProviderPresentationSizeProviding`](/documentation/uikit/uiitemproviderpresentationsizeproviding)

## [See Also](/documentation/UIKit/UIImage#see-also)

### [Representations](/documentation/UIKit/UIImage#Representations)

```swift
```swift
```swift
```swift
class SymbolConfiguration
```
```

An object that contains the specific font, size, style, and weight attributes to apply to a symbol image.
```
```swift
```swift
```swift
class Configuration
```
```

A configuration object that contains the traits that the system uses when selecting the current image variant.
```
```