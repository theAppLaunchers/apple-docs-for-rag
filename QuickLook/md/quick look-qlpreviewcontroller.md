

- Quick Look
-  QLPreviewController 

Class

# QLPreviewController

A specialized view controller for previewing an item.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
class QLPreviewController
```

## Overview

A `QLPreviewController` can display previews for many common file types, including the following:

- iWork documents

- Microsoft Office documents

- Rich text format, or RTF, documents

- PDF files

- Images

- Text files with a uniform type identifier that conforms to the `public.text` type. To learn more, see Uniform Type Identifiers.

- Comma-separated values, or CSV, files

- 3D models in the USDZ format with both standalone and AR views for viewing the model

Note

The list of supported common file types may change between operating system releases. In addition, you can enable previews for your own file types by implementing your own preview extension.

### Providing data to a preview controller

To use a preview controller, you need to provide a data source object. The data source provides preview items to the controller and tells it how many items to include in a preview navigation list. If there’s more than one item in the list, a controller displays navigation arrows to let the user switch among the items. If you push a preview controller into view using a navigation controller, you can provide buttons in the navigation bar for moving through the navigation list.

For details on providing items to a preview controller, see QLPreviewControllerDataSource and QLPreviewItem.

### Presenting a preview controller

You can present a `QLPreviewController` modally by calling present(_:animated:completion:) from a presenting UIViewController, or you can push it into view using a UINavigationController. The preview includes a title that the system derives from the last path component of the item URL. You can override it by implementing a previewItemTitle accessor for the preview item.

### Previewing items in Mac apps built with Mac Catalyst

For Mac apps built with Mac Catalyst, presenting a `QLPreviewController` displays the preview in a QLPreviewPanel and dims the previously active window. However, unlike on iOS devices, where displaying a preview hides the presenting view controller, the previously visible window’s content remains visible in Mac apps built with Mac Catalyst. Be sure the content is appropriate to display while the `QLPreviewPanel` is visible.

In addition, the system doesn’t display a live preview if you embed the `QLPreviewController` in another view controller. Instead, it displays a thumbnail that matches the size of the preview controller’s view.

## Topics

### Configuring a preview controller

var dataSource: (any QLPreviewControllerDataSource)?

The preview controller’s data source.

protocol QLPreviewControllerDataSource

The protocol that a data source for a preview controller needs to adopt to provide preview items to the controller.

var delegate: (any QLPreviewControllerDelegate)?

The preview controller’s delegate object.

protocol QLPreviewControllerDelegate

The protocol that a delegate of a preview controller needs to adopt to handle Quick Look previews.

### Managing item previews

class func canPreview(any QLPreviewItem) -> Bool

Returns a Boolean value that indicates whether the preview controller can display an item.

var currentPreviewItem: (any QLPreviewItem)?

The item displaying in the Quick Look preview controller.

var currentPreviewItemIndex: Int

The index within the preview item navigation list of the item displaying in the Quick Look preview controller.

func refreshCurrentPreviewItem()

Asks the Quick Look preview controller to recompute the display of the current preview item.

func reloadData()

Asks the preview controller to reload its data from its data source.

## Relationships

### Inherits From

- UIViewController

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSExtensionRequestHandling
- NSObjectProtocol
- NSTouchBarProvider
- UIActivityItemsConfigurationProviding
- UIAppearanceContainer
- UIContentContainer
- UIFocusEnvironment
- UIPasteConfigurationSupporting
- UIResponderStandardEditActions
- UIStateRestoring
- UITraitChangeObservable
- UITraitEnvironment
- UIUserActivityRestoring

## See Also

### Previews

protocol QLPreviewItem : NSObjectProtocol

A protocol that defines a set of properties you implement to make a preview of your application’s content.

class QLPreviewSceneActivationConfiguration

A scene configuration to preview items at the specified URLs.

Previews or thumbnail images for macOS 10.14 or earlier

Create thumbnail images or previews of common files and custom file types in earlier versions of macOS.

