*   [UIKit](/documentation/uikit)
*   [UIButton](/documentation/uikit/uibutton)
*   UIButton.Configuration

Structure

# UIButton.Configuration

A configuration that specifies the appearance and behavior of a button and its contents.

iOS 15.0+iPadOS 15.0+Mac CatalysttvOS 15.0+visionOS

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct Configuration
```
```
```
```
```
```
```
```

## [Overview](/documentation/UIKit/UIButton/Configuration-swift.struct#overview)

You can configure and update a button with a [`UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct). A button configuration contains all the customization options available with other methods, such as [`setTitle(_:for:)`](/documentation/uikit/uibutton/settitle\(_:for:\)), and can serve as a replacement for those methods. Alternatively, you can use a configuration in combination with these other methods and adopt new button behaviors and appearance without rewriting your customized [`UIButton`](/documentation/uikit/uibutton) code.

## [Topics](/documentation/UIKit/UIButton/Configuration-swift.struct#topics)

### [Creating configurations](/documentation/UIKit/UIButton/Configuration-swift.struct#Creating-configurations)

[`static func plain() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/plain\(\))

Creates a configuration for a button with a transparent background.

[`static func gray() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/gray\(\))

Creates a configuration for a button with a gray background.

[`static func tinted() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/tinted\(\))

Creates a configuration for a button with a tinted background color.

[`static func filled() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/filled\(\))

Creates a configuration for a button with a background filled with the button’s tint color.

[`static func borderless() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/borderless\(\))

Creates a configuration for a button that has a borderless style.

[`static func bordered() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/bordered\(\))

Creates a configuration for a button that has a bordered style.

[`static func borderedTinted() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/borderedtinted\(\))

Creates a configuration for a button that has a tinted, bordered style.

[`static func borderedProminent() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/borderedprominent\(\))

Creates a configuration for a button that has a prominent, bordered style.

```swift
```swift
```swift
func updated(for: UIButton) -> UIButton.Configuration
```
```

Returns a copy of the configuration, updated for the given button.
```

### [Configuring titles](/documentation/UIKit/UIButton/Configuration-swift.struct#Configuring-titles)

```swift
```swift
```swift
```swift
var title: String?
```
```

The text of the title label the button displays.
```
```swift
```swift
```swift
var subtitle: String?
```
```

The text the subtitle label of the button displays.
```
```swift
```swift
```swift
var attributedTitle: AttributedString?
```
```

The text and style attributes for the button’s title label.
```
```swift
```swift
```swift
var attributedSubtitle: AttributedString?
```
```

The text and style attributes for the button’s subtitle label.
```
```swift
```swift
```swift
var titleTextAttributesTransformer: UIConfigurationTextAttributesTransformer?
```
```

A structure to update the attributed title when the button state changes.
```
```swift
```swift
```swift
var subtitleTextAttributesTransformer: UIConfigurationTextAttributesTransformer?
```
```

A structure to update the attributed subtitle when the button state changes.
```
```swift
```swift
```swift
struct UIConfigurationTextAttributesTransformer
```
```

Defines a text transformation that can affect the visual appearance of a string.
```
```swift
```swift
```swift
var titlePadding: CGFloat
```
```

The distance between the title and subtitle labels.
```
```swift
```swift
```swift
var titleAlignment: UIButton.Configuration.TitleAlignment
```
```

The text alignment the button uses to lay out the title and subtitle.
```
```swift
```swift
```swift
enum TitleAlignment
```
```

Specifies how to align a button’s title and subtitle.
```
```swift
```swift
```swift
var titleLineBreakMode: NSLineBreakMode
```
```

The line break mode the button uses to lay out the button’s title.
```
```swift
```swift
```swift
var subtitleLineBreakMode: NSLineBreakMode
```
```

The line break mode the button uses to lay out the button’s subtitle.
```
```

### [Configuring images](/documentation/UIKit/UIButton/Configuration-swift.struct#Configuring-images)

```swift
```swift
```swift
```swift
var image: UIImage?
```
```

The foreground image the button displays.
```
```swift
```swift
```swift
var imagePadding: CGFloat
```
```

The distance between the button’s image and text.
```
```swift
```swift
```swift
var imagePlacement: NSDirectionalRectEdge
```
```

The edge against which the button places the image.
```
```swift
```swift
```swift
var imageReservation: CGFloat
```
```

A value that reserves space for the image in the same axis as the edge against which the button places the image.
```
```swift
```swift
```swift
var imageColorTransformer: UIConfigurationColorTransformer?
```
```

A block that transforms the image color when the button state changes.
```
```swift
```swift
```swift
var preferredSymbolConfigurationForImage: UIImage.SymbolConfiguration?
```
```

A requested configuration object for the button symbol image.
```
```

### [Configuring layout](/documentation/UIKit/UIButton/Configuration-swift.struct#Configuring-layout)

```swift
```swift
```swift
```swift
var buttonSize: UIButton.Configuration.Size
```
```

A size that requests a preferred size for the button.
```
```swift
```swift
```swift
enum Size
```
```

A predefined size for button elements.
```
```swift
```swift
```swift
var contentInsets: NSDirectionalEdgeInsets
```
```

The distance from the button’s content area to its bounds.
```
```swift
```swift
```swift
func setDefaultContentInsets()
```
```

Restores the default content insets.
```
```

### [Configuring button colors](/documentation/UIKit/UIButton/Configuration-swift.struct#Configuring-button-colors)

```swift
```swift
```swift
```swift
var baseBackgroundColor: UIColor?
```
```

The untransformed color for background views.
```
```swift
```swift
```swift
var baseForegroundColor: UIColor?
```
```

The untransformed color for foreground views.
```
```

### [Configuring the button background](/documentation/UIKit/UIButton/Configuration-swift.struct#Configuring-the-button-background)

```swift
```swift
```swift
```swift
var background: UIBackgroundConfiguration
```
```

The configuration to customize the button background.
```
```swift
```swift
```swift
var cornerStyle: UIButton.Configuration.CornerStyle
```
```

The button style that controls the display behavior of the background corner radius.
```
```swift
```swift
```swift
enum CornerStyle
```
```

Settings that determine the appearance of the background corner radius.
```
```

### [Configuring the indicator](/documentation/UIKit/UIButton/Configuration-swift.struct#Configuring-the-indicator)

```swift
```swift
```swift
```swift
var indicator: UIButton.Configuration.Indicator
```
```

The style of the indicator that appears on the button.
```
```swift
```swift
```swift
enum Indicator
```
```

Constants that determine the style of the indicator that appears on a button.
```
```swift
```swift
```swift
var indicatorColorTransformer: UIConfigurationColorTransformer?
```
```

The color transformer for resolving the indicator color.
```
```

### [Configuring the activity indicator](/documentation/UIKit/UIButton/Configuration-swift.struct#Configuring-the-activity-indicator)

```swift
```swift
```swift
```swift
var showsActivityIndicator: Bool
```
```

A Boolean value that determines whether the button displays an activity indicator instead of an image.
```
```swift
```swift
```swift
var activityIndicatorColorTransformer: UIConfigurationColorTransformer?
```
```

The color transformer for resolving the color of the activity indicator.
```
```

### [Configuring selection behavior](/documentation/UIKit/UIButton/Configuration-swift.struct#Configuring-selection-behavior)

```swift
```swift
```swift
```swift
var automaticallyUpdateForSelection: Bool
```
```

A Boolean value that determines whether the style automatically updates when the button is in a selected state.
```
```

### [Configuring the appearance on macOS](/documentation/UIKit/UIButton/Configuration-swift.struct#Configuring-the-appearance-on-macOS)

```swift
```swift
```swift
```swift
var macIdiomStyle: UIButton.Configuration.MacIdiomStyle
```
```

The style to use when this button appears in macOS.
```
```swift
```swift
```swift
enum MacIdiomStyle
```
```

The button style your app uses when running in macOS.
```
```

### [Instance Properties](/documentation/UIKit/UIButton/Configuration-swift.struct#Instance-Properties)

```swift
```swift
```swift
```swift
var symbolContentTransition: UISymbolContentTransition?
```
```
```
```

### [Type Methods](/documentation/UIKit/UIButton/Configuration-swift.struct#Type-Methods)

[`static func glass() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/glass\(\))

[`static func prominentGlass() -> UIButton.Configuration`](/documentation/uikit/uibutton/configuration-swift.struct/prominentglass\(\))

## [Relationships](/documentation/UIKit/UIButton/Configuration-swift.struct#relationships)

### [Conforms To](/documentation/UIKit/UIButton/Configuration-swift.struct#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)

## [See Also](/documentation/UIKit/UIButton/Configuration-swift.struct#see-also)

### [Creating buttons from a configuration object](/documentation/UIKit/UIButton/Configuration-swift.struct#Creating-buttons-from-a-configuration-object)

[`convenience init(configuration: UIButton.Configuration, primaryAction: UIAction?)`](/documentation/uikit/uibutton/init\(configuration:primaryaction:\))

Creates a new button with the specified configuration and registers the primary action event.