

- AppKit
- NSButtonCell
-  attributedTitle 

Instance Property

# attributedTitle

The title displayed by the button when it’s in its normal state as an attributed string.

macOS

``` source
@NSCopying @MainActor
var attributedTitle: NSAttributedString { get set }
```

## Discussion

The value of this property is the attributes string that appears on the button when it’s in its normal state, or an empty attributed string if the button doesn’t display a title. A button’s title is always displayed if the button doesn’t use its alternate contents for highlighting or displaying the alternate state. By default, a button’s title is “Button.” Setting this property redraws the button if necessary.

Graphics attributes configured for the cell (such as `backgroundColor`, `alignment`, `font`, and so on) are overridden when corresponding properties are set for the attributed string.

## See Also

### Related Documentation

var font: NSFont?

The font that the cell uses to display text.

func setButtonType(NSButton.ButtonType)

Sets how the button highlights while pressed and how it shows its state.

### Setting Titles

var alternateTitle: String

The string displayed by the button when it’s in its alternate state.

var attributedAlternateTitle: NSAttributedString

The title displayed by the button when it’s in its alternate state, as an attributed string.

var title: String!

The title displayed on the button when it’s in its normal state.

