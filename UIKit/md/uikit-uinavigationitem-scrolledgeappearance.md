

- UIKit
- UINavigationItem
-  scrollEdgeAppearance 

Instance Property

# scrollEdgeAppearance

The appearance settings for a standard-height navigation bar when the edge of scrollable content aligns with the edge of the navigation bar.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
@NSCopying @MainActor
var scrollEdgeAppearance: UINavigationBarAppearance? { get set }
```

## Discussion

When the navigation bar displays the top navigation item, the appearance settings in this property override the settings provided by the scrollEdgeAppearance property of UINavigationBar.

Use this property to apply appearance settings to the navigation bar based on the navigation item stored in the topItem property. If the top item’s scrollEdgeAppearance property is `nil`, UIKit uses the navigation bar’s scroll edge appearance.

When running on apps that use iOS 14 or earlier, this property applies to navigation bars with large titles. In iOS 15, this property applies to all navigation bars.

## See Also

### Overriding the navigation bar’s appearance settings

var standardAppearance: UINavigationBarAppearance?

The appearance settings for a standard-height navigation bar.

var compactAppearance: UINavigationBarAppearance?

The appearance settings for a compact-height navigation bar.

var compactScrollEdgeAppearance: UINavigationBarAppearance?

The appearance settings for a compact-height navigation bar when the edge of scrollable content aligns with the edge of the navigation bar.

