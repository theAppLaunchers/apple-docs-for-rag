*   [PhotosUI](/documentation/photosui)
*   PHPickerConfiguration

Structure

# PHPickerConfiguration

An object that contains information about how to configure a picker view controller.

iOS 14.0+iPadOS 14.0+Mac CatalystmacOS 13.0+visionOS

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct PHPickerConfiguration
```
```
```
```
```
```
```
```

## [Topics](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#topics)

### [Creating a configuration](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#Creating-a-configuration)

[`init()`](/documentation/photosui/phpickerconfiguration-swift.struct/init\(\))

Creates a new configuration object.

[`init(photoLibrary: PHPhotoLibrary)`](/documentation/photosui/phpickerconfiguration-swift.struct/init\(photolibrary:\))

Creates a new configuration object for a photo library.

### [Filtering asset types](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#Filtering-asset-types)

```swift
```swift
```swift
```swift
var filter: PHPickerFilter?
```
```

The filter you apply to restrict the asset types the picker displays.
```
```swift
```swift
```swift
struct PHPickerFilter
```
```

A type that defines the filter to apply to the photo library.
```
```

### [Selecting the preferred asset representation](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#Selecting-the-preferred-asset-representation)

```swift
```swift
```swift
```swift
var preferredAssetRepresentationMode: PHPickerConfiguration.AssetRepresentationMode
```
```

A mode that determines which representation to use if an asset contains more than one.
```
```swift
```swift
```swift
enum AssetRepresentationMode
```
```

Constants identifying the mode the system uses when many representations exist for an asset.
```
```

### [Preselecting assets](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#Preselecting-assets)

```swift
```swift
```swift
```swift
var preselectedAssetIdentifiers: [String]
```
```

An array of asset identifiers to preselect in the picker.
```
```

### [Setting the selection limit](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#Setting-the-selection-limit)

```swift
```swift
```swift
```swift
var selectionLimit: Int
```
```

The maximum number of selections the user can make.
```
```swift
```swift
```swift
var selection: PHPickerConfiguration.Selection
```
```

The selection behavior for the picker.
```
```swift
```swift
```swift
enum PHPickerConfigurationSelection
```
```

Options that represent differing selection behavior.
```
```swift
```swift
```swift
enum Selection
```
```

Options that represent differing selection behavior.
```
```

### [Customizing picker appearance and behavior](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#Customizing-picker-appearance-and-behavior)

```swift
```swift
```swift
```swift
var mode: PHPickerMode
```
```

A layout type for the photos in the picker’s view.
```
```swift
```swift
```swift
struct PHPickerMode
```
```

Layout options that determine how the picker orders photos visually.
```
```swift
```swift
```swift
var disabledCapabilities: PHPickerCapabilities
```
```

The aspects of a photo picker’s default appearance that your app can disable.
```
```swift
```swift
```swift
struct PHPickerCapabilities
```
```

Options that customize the look and behavior of the photos picker.
```
```swift
```swift
```swift
var edgesWithoutContentMargins: NSDirectionalRectEdge
```
```

The portions of a photo picker’s perimeter that are borderless.
```
```swift
```swift
```swift
struct Update
```
```

An object that defines the aspects of a photo picker’s appearance that can change while it’s presented.
```
```

## [Relationships](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#relationships)

### [Conforms To](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#conforms-to)

*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#see-also)

### [Photos picker for UIKit, AppKit](/documentation/PhotosUI/PHPickerConfiguration-swift.struct#Photos-picker-for-UIKit-AppKit)

[

Selecting Photos and Videos in iOS](/documentation/photokit/selecting-photos-and-videos-in-ios)

Improve the user experience of finding and selecting assets by using the Photos picker.

```swift
```swift
```swift
class PHPickerViewController
```
```

A view controller that provides the user interface for choosing assets from the photo library.
```
```swift
```swift
```swift
protocol PHPickerViewControllerDelegate
```
```

A set of methods that the delegate must implement to respond to `PHPickerViewController` user events.
```
```swift
```swift
```swift
struct PHPickerFilter
```
```

A type that defines the filter to apply to the photo library.
```
```swift
```swift
```swift
struct PHPickerResult
```
```

Types that represent a selected asset from the user’s photo library.
```