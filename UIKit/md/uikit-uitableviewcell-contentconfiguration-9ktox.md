

- UIKit
- UITableViewCell
-  contentConfiguration 

Instance Property

# contentConfiguration

The current content configuration of the cell.

iOS 14.0+iPadOS 14.0+Mac CatalysttvOS 14.0+visionOS

``` source
@MainActor @preconcurrency
var contentConfiguration: (any UIContentConfiguration)? { get set }
```

## Discussion

Using a content configuration, you can set the cell’s content and styling for a variety of different cell states. You can get the default configuration using defaultContentConfiguration(), assign your content to the configuration, customize any other properties, and assign it to the view as the current contentConfiguration.

Setting a content configuration replaces the existing contentView of the cell with a new content view instance from the configuration, or directly applies the configuration to the existing content view if the configuration is compatible with the existing content view type.

The default value is `nil`. After you set a content configuration to this property, setting this property back to `nil` replaces the current content view with a new, empty content view.

## See Also

### Managing the content

func defaultContentConfiguration() -> UIListContentConfiguration

Retrieves a default list content configuration for the cell’s style.

var automaticallyUpdatesContentConfiguration: Bool

A Boolean value that determines whether the cell automatically updates its content configuration when its state changes.

var contentView: UIView

The content view of the cell object.

