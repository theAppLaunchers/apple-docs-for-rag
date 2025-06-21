*   [VisionKit](/documentation/visionkit)
*   Enabling Live Text interactions with images

Article

# Enabling Live Text interactions with images

Add a Live Text interface that enables users to perform actions with text and QR codes that appear in images.

## [Overview](/documentation/VisionKit/enabling-live-text-interactions-with-images#Overview)

Enhance the user experience with images in your app by adding standard Live Text interactions. Live Text lets users tap text in an image to copy it, make a call, send an email, translate it, or look up directions. VisionKit provides this familiar Live Text interface to your images and across platforms.

For iOS apps, users can use a long-press gesture (touch and hold) a QR code to follow a link or take another action, depending on the payload. The payload is the data that a QR code contains, such as a URL or email address.

Before interacting with items in an image, the user can tap the Live Text button in the lower-right corner to highlight the recognized items. Then a data-specific action menu appears when the user double-taps on text in an image, and uses a long-press gesture on an email address or QR code.

![A mockup of three iPhone screens showing the Live Text button and highlighted text with its action menu, a long press of an email address with its action menu, and a long press of a QR code with its action menu.](https://docs-assets.developer.apple.com/published/18bb3f1f13bfb8d615897f3714d561f9/enabling_live_text_interactions_with_images-1%402x.png)

In your app, you decide whether Live Text recognizes text and data within text, and for iOS apps, QR codes in the image. You choose the types of items to look for and run the analysis on the image, and then VisionKit provides the entire Live Text interface with the breadth of actions for specific types.

Important

The code listings in this article use asynchronous methods that you invoke from an `async` method or within a [`Task`](/documentation/Swift/Task) structure. For details on asynchronous flows, see [Concurrency](/documentation/Swift/concurrency).

### [Check whether the device supports Live Text](/documentation/VisionKit/enabling-live-text-interactions-with-images#Check-whether-the-device-supports-Live-Text)

Before showing a Live Text interface in your app, check whether the device supports Live Text. For iOS apps, the image analyzer is available only on devices with the A12 Bionic chip and later. If the `ImageAnalyzer` [`isSupported`](/documentation/visionkit/imageanalyzer/issupported) property is `true`, show the Live Text interface. Otherwise, disable any feature in your app that relies on Live Text. If you attempt to start the Live Text interface when this property is `false`, the interface doesn’t appear.

### [Add a Live Text interaction object to your view in iOS](/documentation/VisionKit/enabling-live-text-interactions-with-images#Add-a-Live-Text-interaction-object-to-your-view-in-iOS)

For iOS apps, you add the Live Text interface by adding an interaction object to the view containing the image. If you use a [`UIImageView`](/documentation/UIKit/UIImageView) to display the image, it handles the image content area calculations for you.

Add an [`ImageAnalysisInteraction`](/documentation/visionkit/imageanalysisinteraction) object directly on the view containing the image.

```swift
```swift
```swift
```swift
```swift
```swift
let interaction = ImageAnalysisInteraction()
```
```
imageView.addInteraction(interaction)
```
```
```
```

Optionally, customize the interface by setting the interaction’s delegate to an object that implements the [`ImageAnalysisInteractionDelegate`](/documentation/visionkit/imageanalysisinteractiondelegate) protocol methods.

```

```
interaction.delegate = self
```

```

If you don’t use a [`UIImageView`](/documentation/UIKit/UIImageView) object, inform the interaction object when the content area of the image changes while the interaction bounds don’t change. Implement the `ImageAnalysisInteractionDelegate` [`contentsRect(for:)`](/documentation/visionkit/imageanalysisinteractiondelegate/contentsrect\(for:\)) protocol method to return the content area of the image. This keeps the Live Text highlights within the bounds of the image. Then use the [`setContentsRectNeedsUpdate()`](/documentation/visionkit/imageanalysisinteraction/setcontentsrectneedsupdate\(\)) method to notify the interaction if the content area changes.

### [Add a Live Text view to your image view in macOS](/documentation/VisionKit/enabling-live-text-interactions-with-images#Add-a-Live-Text-view-to-your-image-view-in-macOS)

For macOS apps, add the Live Text interface by adding a view above the view containing the image. If you use an [`NSImageView`](/documentation/AppKit/NSImageView) to display the image, it handles the image content area calculations for you.

First create an instance of the [`ImageAnalysisOverlayView`](/documentation/visionkit/imageanalysisoverlayview) class.

```swift
```swift
```swift
```swift
```swift
```swift
let overlayView = ImageAnalysisOverlayView()
```
```
```
```
```
```

Then configure the overlay view to fit the bounds of the image. If your view is an image view, set the [`trackingImageView`](/documentation/visionkit/imageanalysisoverlayview/trackingimageview) property so that the dimensions adjust when the scaling and alignment properties change.

```

```
overlayView.autoresizingMask = [.width, .height]
overlayView.frame = imageView.bounds
overlayView.trackingImageView = imageView
```

```

Add the overlay view above the image in the hierarchy. For example, add it as a subview of the view containing the image.

```

```
imageView.addSubview(overlayView)
```

```

To customize the interface, set the overlay view’s delegate to an object that implements the optional [`ImageAnalysisOverlayViewDelegate`](/documentation/visionkit/imageanalysisoverlayviewdelegate) protocol methods.

```

```
overlayView.delegate = self
```

```

Implement the [`overlayView(_:shouldBeginAt:forAnalysisType:)`](/documentation/visionkit/imageanalysisoverlayviewdelegate/overlayview\(_:shouldbeginat:foranalysistype:\)-35czq) protocol method to return `true` to begin the interaction.

```swift
```swift
```swift
```swift
```swift
```swift
func overlayView(_ overlayView: ImageAnalysisOverlayView,
```
```
 
           shouldBeginAt point: CGPoint, forAnalysisType 
           analysisType: ImageAnalysisOverlayView.InteractionTypes) -> Bool { 
    overlayView.hasInteractiveItem(at: point) || 
    overlayView.hasActiveTextSelection 
}
```
```
```
```

If you aren’t using an [`NSImageView`](/documentation/AppKit/NSImageView) object, implement the `ImageAnalysisOverlayViewDelegate` [`contentsRect(for:)`](/documentation/visionkit/imageanalysisoverlayviewdelegate/contentsrect\(for:\)-34yzu) protocol method to return the content area of the image. Then use the [`setContentsRectNeedsUpdate()`](/documentation/visionkit/imageanalysisoverlayview/setcontentsrectneedsupdate\(\)) method to notify the overlay view if the content area of the image changes while the view bounds don’t change.

![A diagram showing an image that is offset in an arbitrary view with the overlay view on top of it.](https://docs-assets.developer.apple.com/published/81c2d3481475ede1fb5f15419f88f2ec/enabling_live_text_interactions_with_images-2%402x.png)

### [Find items and start the interaction with an image](/documentation/VisionKit/enabling-live-text-interactions-with-images#Find-items-and-start-the-interaction-with-an-image)

Process the image that your view displays using an [`ImageAnalyzer`](/documentation/visionkit/imageanalyzer) object. First, specify the types of items in the image you want to find when you create an [`ImageAnalyzer.Configuration`](/documentation/visionkit/imageanalyzer/configuration) object. For iOS apps, the analyzer recognizes both text and machine-readable QR codes in an image; for macOS apps, the analyzer recognizes text in an image.

```swift
```swift
```swift
```swift
```swift
```swift
let configuration = ImageAnalyzer.Configuration([.text, .machineReadableCode])
```
```
```
```
```
```

Then analyze the image by sending [`analyze(_:configuration:)`](/documentation/visionkit/imageanalyzer/analyze\(_:configuration:\)) to an [`ImageAnalyzer`](/documentation/visionkit/imageanalyzer) object, passing the image and the configuration. To improve performance, use a single shared instance of the analyzer throughout the app.

```swift
```swift
```swift
```swift
```swift
```swift
let analyzer = ImageAnalyzer()
```
```
```swift
```swift
let analysis = try? await analyzer.analyze(image, configuration: configuration)
```
```
```
```
```
```

For iOS apps, start the Live Text interface by setting the [`analysis`](/documentation/visionkit/imageanalysisinteraction/analysis) property of the [`ImageAnalysisInteraction`](/documentation/visionkit/imageanalysisinteraction) object to the results of the analyze method. For example, set the [`analysis`](/documentation/visionkit/imageanalysisinteraction/analysis) property in the action method of a control that starts Live Text.

```

```
interaction.analysis = analysis
```

```

For macOS apps, start the Live Text interface by setting the [`analysis`](/documentation/visionkit/imageanalysisoverlayview/analysis) property of the [`ImageAnalysisOverlayView`](/documentation/visionkit/imageanalysisoverlayview) object.

```

```
overlayView.analysis = analysis
```

```

The standard Live Text menu appears when users click and hold items in the image. The user chooses actions from this menu, depending on the type of item.

### [Customize behavior using interaction types](/documentation/VisionKit/enabling-live-text-interactions-with-images#Customize-behavior-using-interaction-types)

You can change the behavior of the interface by enabling types of interactions with items the analyzer finds in the image. If you set the interaction or overlay view [`preferredInteractionTypes`](/documentation/visionkit/imageanalysisinteraction/preferredinteractiontypes) property to [`automatic`](/documentation/visionkit/imageanalysisinteraction/interactiontypes/automatic), users can interact with all types of items that the analyzer finds.

```

```
interaction.preferredInteractionTypes = .automatic
```

```

If you set the [`preferredInteractionTypes`](/documentation/visionkit/imageanalysisinteraction/preferredinteractiontypes) property to just [`textSelection`](/documentation/visionkit/imageanalysisinteraction/interactiontypes/textselection), users can only select text in the image and then perform a basic text action, such as copying, translating, or sharing the text. For iOS apps, if the [`ImageAnalysisInteraction`](/documentation/visionkit/imageanalysisinteraction) object’s [`allowLongPressForDataDetectorsInTextMode`](/documentation/visionkit/imageanalysisinteraction/allowlongpressfordatadetectorsintextmode) property is `true`, users can also touch and hold text that contains data (URLs, phone numbers, and email addresses) to perform a data-specific action.

For iOS apps, users can tap the Live Text button in the lower-right corner to switch to highlight mode. Then users can touch and hold data that the analyzer detects in text to perform a data-specific action, such as opening a URL, calling a phone number, or sending an email.

![A mockup of the lower half of an iPhone screen showing the Live Text button enabled and recognized items highlighted, such as a mailing address and QR code.](https://docs-assets.developer.apple.com/published/db02b7be0de6b19bc1dd36bc19293691/enabling_live_text_interactions_with_images-3%402x.png)

To let users interact with data that the analyzer detects in text in macOS, set the [`preferredInteractionTypes`](/documentation/visionkit/imageanalysisoverlayview/preferredinteractiontypes) property to [`dataDetectors`](/documentation/visionkit/imageanalysisoverlayview/interactiontypes/datadetectors). Then users can hover over data in text to perform a data-specific action.

For iOS apps only, users can touch and hold QR codes and perform an action, depending on the payload, such as following an embedded link. To enable QR code interactions, set the [`ImageAnalyzer.Configuration`](/documentation/visionkit/imageanalyzer/configuration) structure’s [`analysisTypes`](/documentation/visionkit/imageanalyzer/configuration/analysistypes) property to [`machineReadableCode`](/documentation/visionkit/imageanalyzer/analysistypes/machinereadablecode).

### [Change the supplementary interface](/documentation/VisionKit/enabling-live-text-interactions-with-images#Change-the-supplementary-interface)

You can modify the Live Text supplementary interface to conform better to the look of your app. The supplementary interface consists of the quick actions in the lower-left corner and the Live Text button in the lower-right corner of the interface.

To hide the supplementary interface, set the [`isSupplementaryInterfaceHidden`](/documentation/visionkit/imageanalysisinteraction/issupplementaryinterfacehidden) to `false`. For iOS apps, if the [`allowLongPressForDataDetectorsInTextMode`](/documentation/visionkit/imageanalysisinteraction/allowlongpressfordatadetectorsintextmode) property is `true`, users can still touch and hold text to perform data-specific actions.

If your interface overlaps the supplementary interface, set the [`supplementaryInterfaceContentInsets`](/documentation/visionkit/imageanalysisinteraction/supplementaryinterfacecontentinsets) property appropriately to move the quick actions and Live Text button.

If you want the supplementary interface to use a custom font, set the [`supplementaryInterfaceFont`](/documentation/visionkit/imageanalysisinteraction/supplementaryinterfacefont) property. Quick actions use the specified font for text and font weight for symbols. For button size consistency, the Live Text interface ignores the point size.

### [Specify recognized languages](/documentation/VisionKit/enabling-live-text-interactions-with-images#Specify-recognized-languages)

By default the image analyzer attempts to recognize the user’s preferred languages. If you want the analyzer to consider other languages, set the [`locales`](/documentation/visionkit/imageanalyzer/configuration/locales) property of the [`ImageAnalyzer.Configuration`](/documentation/visionkit/imageanalyzer/configuration) object.

To determine whether the image analyzer supports a language, check whether the array that the `ImageAnalyzer` [`supportedTextRecognitionLanguages`](/documentation/visionkit/imageanalyzer/supportedtextrecognitionlanguages) class property returns includes the language ID.

For more information on language IDs, see [Choosing localization regions and scripts](/documentation/Xcode/choosing-localization-regions-and-scripts).

## [See Also](/documentation/VisionKit/enabling-live-text-interactions-with-images#see-also)

### [Content recognition and interaction in images](/documentation/VisionKit/enabling-live-text-interactions-with-images#Content-recognition-and-interaction-in-images)

```swift
```swift
```swift
```swift
class ImageAnalyzer
```
```

An object that finds items in images that people can interact with, such as subjects, text, and QR codes.
```
```swift
```swift
```swift
class ImageAnalysis
```
```

An object that represents the results of analyzing an image, and provides the input for the Live Text interface object.
```
```swift
```swift
```swift
class ImageAnalysisInteraction
```
```

An interface that enables people to interact with recognized text, barcodes, and other objects in an image.
```
```swift
```swift
```swift
protocol ImageAnalysisInteractionDelegate
```
```

A delegate that handles image-analysis and user-interaction callbacks for an interaction object.
```
```swift
```swift
```swift
class ImageAnalysisOverlayView
```
```

A view that enables people to interact with recognized text, barcodes, and other objects in an image.
```
```swift
```swift
```swift
protocol ImageAnalysisOverlayViewDelegate
```
```

A delegate that handles image-analysis and user-interaction callbacks for an overlay view.
```
```