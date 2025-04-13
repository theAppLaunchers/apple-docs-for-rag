

- UIKit
- UIButton
-  tintColor 

Instance Property

# tintColor

The tint color to apply to the button title and image.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
var tintColor: UIColor! { get set }
```

## Discussion

All subclasses of UIView derive their behavior for tintColor from the base class. See the discussion of tintColor at the UIView level for more information.

This property has no default effect for buttons with type UIButton.ButtonType.custom. For custom buttons, you must implement any behavior related to tintColor yourself.

## See Also

### Managing images and tint color

func backgroundImage(for: UIControl.State) -> UIImage?

Returns the background image used for a button state.

func image(for: UIControl.State) -> UIImage?

Returns the image used for a button state.

func setBackgroundImage(UIImage?, for: UIControl.State)

Sets the background image to use for the specified button state.

func setImage(UIImage?, for: UIControl.State)

Sets the image to use for the specified state.

func preferredSymbolConfigurationForImage(in: UIControl.State) -> UIImage.SymbolConfiguration?

Returns the preferred symbol configuration for a button state.

func setPreferredSymbolConfiguration(UIImage.SymbolConfiguration?, forImageIn: UIControl.State)

Sets the preferred symbol configuration for a button state.

