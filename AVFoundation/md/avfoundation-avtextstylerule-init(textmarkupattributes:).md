

- AVFoundation
- AVTextStyleRule
-  init(textMarkupAttributes:) 

Initializer

# init(textMarkupAttributes:)

Creates a text style rule object with the specified style attributes.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+

``` source
convenience init?(textMarkupAttributes: [String : Any] = [:])
```

## Parameters 

`textMarkupAttributes`  

A dictionary of style attributes. For a list of supported keys and values that you can include in this dictionary, see `CMTextMarkup.h`.

## Return Value

A text style rule object initialized with the specified attributes.

## Discussion

This method sets the textSelector property of the style object to `nil`, which causes the rules to be applied to all of the text in the media item.

## See Also

### Creating and Initializing Style Rules

class func textStyleRules(fromPropertyList: Any) -> [AVTextStyleRule]?

Creates an array of text style rule objects from the specified property-list object.

init?(textMarkupAttributes: [String : Any], textSelector: String?)

Creates a text style rule object with the specified style attributes and text range information.

