*   [UIKit](/documentation/uikit)
*   UIContentUnavailableConfiguration

Structure

# UIContentUnavailableConfiguration

A content configuration for a content-unavailable view.

iOS 17.0+iPadOS 17.0+Mac CatalysttvOS 17.0+visionOS

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct UIContentUnavailableConfiguration
```
```
```
```
```
```
```
```

## [Overview](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#overview)

A content-unavailable configuration is a composable description of a view that indicates your app can’t display content. Using a content-unavailable configuration, you can obtain system default styling for a variety of different empty states. Fill the configuration with placeholder content, and then assign it to a view controller’s [`contentUnavailableConfiguration`](/documentation/uikit/uiviewcontroller/contentunavailableconfiguration-4b95e), or to a [`UIContentUnavailableView`](/documentation/uikit/uicontentunavailableview).

The following screenshot shows an example of a content-unavailable view configured by setting the [`image`](/documentation/uikit/uicontentunavailableconfiguration-swift.struct/image), [`text`](/documentation/uikit/uicontentunavailableconfiguration-swift.struct/text), and [`secondaryText`](/documentation/uikit/uicontentunavailableconfiguration-swift.struct/secondarytext) properties.

![A screenshot of a content-unavailable view indicating that a user has no files in the iCloud Drive Downloads folder.](https://docs-assets.developer.apple.com/published/7c656513bf8e80dc345aa2d89f317248/media-4274239%402x.png)

## [Topics](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#topics)

### [Structures](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#Structures)

```swift
```swift
```swift
```swift
struct ButtonProperties
```
```

Properties to configure buttons for a content-unavailable view.
```
```swift
```swift
```swift
struct ImageProperties
```
```

Properties to configure the image for a content-unavailable view.
```
```swift
```swift
```swift
struct TextProperties
```
```

Properties to configure text for a content-unavailable view.
```
```

### [Instance Properties](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#Instance-Properties)

```swift
```swift
```swift
```swift
var alignment: UIContentUnavailableConfiguration.Alignment
```
```

The alignment of the image, text, and buttons.
```
```swift
```swift
```swift
var attributedText: NSAttributedString?
```
```

An attributed variant of the primary text.
```
```swift
```swift
```swift
var axesPreservingSuperviewLayoutMargins: UIAxis
```
```

Configures which margins use the layout margins inherited from the superview.
```
```swift
```swift
```swift
var background: UIBackgroundConfiguration
```
```

The configuration for the background.
```
```swift
```swift
```swift
var button: UIButton.Configuration
```
```

The configuration for the primary button.
```
```swift
```swift
```swift
var buttonProperties: UIContentUnavailableConfiguration.ButtonProperties
```
```

Additional configuration for the primary button.
```
```swift
```swift
```swift
var buttonToSecondaryButtonPadding: CGFloat
```
```

The padding between the primary button and secondary button.
```
```swift
```swift
```swift
var directionalLayoutMargins: NSDirectionalEdgeInsets
```
```

The margins between the content and the edges of the content view.
```
```swift
```swift
```swift
var image: UIImage?
```
```

The image to display.
```
```swift
```swift
```swift
var imageProperties: UIContentUnavailableConfiguration.ImageProperties
```
```

The configuration for the image.
```
```swift
```swift
```swift
var imageToTextPadding: CGFloat
```
```

The padding between the image and the primary text.
```
```swift
```swift
```swift
var secondaryAttributedText: NSAttributedString?
```
```

An attributed variant of the secondary text.
```
```swift
```swift
```swift
var secondaryButton: UIButton.Configuration
```
```

The configuration for the secondary button.
```
```swift
```swift
```swift
var secondaryButtonProperties: UIContentUnavailableConfiguration.ButtonProperties
```
```

Additional configuration for the secondary button.
```
```swift
```swift
```swift
var secondaryText: String?
```
```

The secondary text to display.
```
```swift
```swift
```swift
var secondaryTextProperties: UIContentUnavailableConfiguration.TextProperties
```
```

Properties for configuring the secondary text.
```
```swift
```swift
```swift
var text: String?
```
```

The primary text to display.
```
```swift
```swift
```swift
var textProperties: UIContentUnavailableConfiguration.TextProperties
```
```

Properties for configuring the primary text.
```
```swift
```swift
```swift
var textToButtonPadding: CGFloat
```
```

The padding between the text and buttons.
```
```swift
```swift
```swift
var textToSecondaryTextPadding: CGFloat
```
```

The padding between the primary and secondary text.
```
```

### [Type Methods](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#Type-Methods)

[`static func empty() -> UIContentUnavailableConfiguration`](/documentation/uikit/uicontentunavailableconfiguration-swift.struct/empty\(\))

Creates the default configuration for unavailable content.

[`static func loading() -> UIContentUnavailableConfiguration`](/documentation/uikit/uicontentunavailableconfiguration-swift.struct/loading\(\))

Creates the default configuration for content that’s loading.

[`static func search() -> UIContentUnavailableConfiguration`](/documentation/uikit/uicontentunavailableconfiguration-swift.struct/search\(\))

Creates the default configuration for searches that return no results.

### [Enumerations](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#Enumerations)

```swift
```swift
```swift
```swift
enum Alignment
```
```

Constants to define the alignment of views in a content-unavailable view.
```
```

## [Relationships](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#relationships)

### [Conforms To](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomReflectable`](/documentation/Swift/CustomReflectable)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`UIContentConfiguration`](/documentation/uikit/uicontentconfiguration-9eib5)

## [See Also](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#see-also)

### [Unavailable content configurations](/documentation/UIKit/UIContentUnavailableConfiguration-swift.struct#Unavailable-content-configurations)

```swift
```swift
```swift
```swift
struct UIContentUnavailableConfigurationState
```
```

A structure that encapsulates state for a content-unavailable view.
```
```