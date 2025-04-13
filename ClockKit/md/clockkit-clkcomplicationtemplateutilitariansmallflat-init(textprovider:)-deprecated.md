

- ClockKit
- CLKComplicationTemplateUtilitarianSmallFlat
-  init(textProvider:) Deprecated

Initializer

# init(textProvider:)

Creates a new template that has a single line of text.

watchOS 7.0–9.0Deprecated

``` source
init(textProvider: CLKTextProvider)
```

## Parameters 

`textProvider`  

The text provider for a single line of text. For multicolor faces, like the Utility face, the system uses the text provider’s tint color for the text. For other faces, the system ignores the provided tint color, and uses a system color instead.

## See Also

### Creating the Template

init(textProvider: CLKTextProvider, imageProvider: CLKImageProvider?)

Creates a new template that has a single row with an image and a line of text.

Deprecated

