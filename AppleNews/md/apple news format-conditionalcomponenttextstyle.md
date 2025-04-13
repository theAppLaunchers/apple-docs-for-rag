

- Apple News Format
-  ConditionalComponentTextStyle 

Object

# ConditionalComponentTextStyle

The object for defining conditional properties for a component text style, and when the conditional properties are in effect.

Apple News Format 1.9+

``` source
object ConditionalComponentTextStyle
```

## Properties

`conditions`

`(`Condition` | [`Condition`])`

 (Required) 

An instance or array of conditions that, when met, cause the conditional component text style properties to take effect.

Possible types: Condition`, ``[`Condition`]`

`backgroundColor`

`(`Color` | string("none"))`

The background color for text lines. This value defaults to transparent.

To remove a previously set condition, use `none`.

Possible types: Color`, ``string("none")`

`dropCapStyle`

`(`DropCapStyle` | string("none"))`

The style of drop cap to apply to the first paragraph of the component.

To remove a previously set condition, use `none`.

Possible types: DropCapStyle`, ``string("none")`

`firstLineIndent`

`integer`

The indent, in points, of the first line of each paragraph.

`fontFamily`

`(string | string("system"))`

The font family to use for text rendering; for example, `Gill` `Sans`. Using a combination of `fontFamily`, `fontWeight`, and `fontStyle`, you can define the appearance of the text. Apple News automatically selects the appropriate font variant from the available variants in that family. See Applying Apple News Format Fonts.

You can use the value `system` to show text in the default font the operating system uses.

Possible types: `string``, ``string("system")`

`fontName`

`string`

The font name to use to refer to an explicit font variant’s PostScript name, such as `GillSans-Bold`. Alternatively, you can use a combination of `fontFamily`, `fontWeight`, and `fontStyle` to have Apple News automatically select the appropriate variant depending on the text formatting used.

See Applying Apple News Format Fonts.

`fontScaling`

`boolean`

A Boolean value that indicates whether scaling of font sizes for various screen sizes is enabled. By default, all font sizes in Apple News Format are scaled down on smaller screen sizes.

Default: `true`

`fontSize`

`integer`

The size of the font, in points. By default, the font size is inherited from a parent component or a default style. As a best practice, try not to go below 16 points for body text. Apple News may automatically resize the `fontSize` for different device sizes or for iOS and iPadOS devices with Larger Accessibility Sizes enabled.

`fontStyle`

`string`

The font style to apply for the selected font.

Valid values:

- `normal`. Selects from the font family a font that Apple News defines as normal.

- `italic`. Selects from the font family a font that Apple News defines as italic. If the family doesn’t contain an italic font variant, but contains an oblique variant, Apple news selects `oblique` instead.

- `oblique`. Selects from the font family a font that Apple News defines as oblique. If the family does not contain an oblique font variant, but contains an italic variant, Apple News selects `italic` instead.

Possible Values: `normal, italic, oblique`

`fontWeight`

`(integer | string)`

The font weight to apply for the selected font. In addition to explicit weights (named or numerical), `lighter` and `bolder` are available, to set text in a lighter or bolder font as compared to the surrounding text.

If Apple News can’t find a font variant with the given specifications in the provided font family, it selects an alternative with the closest match. If Apple News doesn’t find a bold/bolder font, it doesn’t create a faux-bold alternative, and instead uses the closest match. Similarly, if Apple News can’t find an italic or oblique font variant, it won’t slant text or make it appear italicized.

Valid values:

- `thin` or `100`. Thin or hairline weight.

- `extra-light`, `ultra-light` or `200`. Extra-light or ultra-light weight.

- `light` or `300`. Light weight.

- `regular`, `normal`, `book`, `roman`, or `400`. Regular weight. This is the default if no weight is defined or inherited.

- `medium` or `500`. Medium weight.

- `semi-bold`, `demi-bold`, or `600`. Semi-bold or demi-bold weight.

- `bold` or `700`. Bold weight. This is the default when using `` or `` tags in HTML with default `fontWeight`.

- `extra-bold`, `ultra-bold`, or `800`. Extra-bold or ultra-bold weight.

- `black`, `heavy`, or `900`. Black or heavy weight.

- `lighter`. A weight lighter than its surrounding text. When you make surrounding text bold, a value of `lighter` makes it medium.

- `bolder`. A weight heavier than its surrounding text. When you make surrounding text light, a value of `bolder` makes it regular.

Possible types: `integer``, ``string`

Possible Values: `100, 200, 300, 400, 500, 600, 700, 800, 900, thin, extra-light, extralight, ultra-light, light, regular, normal, book, roman, medium, semi-bold, semibold, demi-bold, demibold, bold, extra-bold, extrabold, ultra-bold, ultrabold, black, heavy, lighter, bolder`

`fontWidth`

`string`

The font width for the selected font (known in CSS as font-stretch). This value defines the width characteristics of a font variant between normal, condensed, and expanded. Some font families are categorized by width (for example, `Avenir Next` and `Avenir Next Condensed`), so make sure that the font family you select supports the specified font width.

Valid values:

- `ultra-condensed`. The most condensed variant.

- `extra-condensed`. A very condensed variant.

- `condensed`. A condensed variant.

- `semi-condensed`. A semi-condensed variant.

- `normal` (default). The font variant classified as normal.

- `semi-expanded`. A semi-expanded variant.

- `expanded`. An expanded variant.

- `extra-expanded`. A very expanded variant.

- `ultra-expanded`. The most expanded variant.

Possible Values: `ultra-compressed, extra-compressed, compressed, ultra-condensed, extra-condensed, condensed, semi-condensed, normal, semi-expanded, expanded, extra-expanded, ultra-expanded`

`hangingPunctuation`

`boolean`

A Boolean that defines whether Apple News positions punctuation outside the margins of the body text.

Default: `false`

`hyphenation`

`boolean`

A Boolean that indicates whether Apple News hyphenates text when necessary. By default, only components with the role `body` or `intro` have hyphenation enabled. All other components default to `false`.

`hyphenationMinimumCharactersAfter`

`integer`

The minimum number of characters required after the hyphen to enable hyphenation.

Default: `3`

`hyphenationMinimumCharactersBefore`

`integer`

The minimum number of characters required before the hyphen to enable hyphenation for a word.

Default: `3`

`hyphenationMinimumWordLength`

`integer`

The minimum number of characters required to enable hyphenation for a word.

Default: `0`

`hyphenationZone`

`integer`

The area in points from the right edge of the text component before which a word needs to start to enable hyphenation.

By default, the value is set to 18 points.

A larger value reduces the allowable hyphenation area of a word, which can result in a more ragged appearance of the text along the right margin.

Default: `18`

`lineBalancing`

`boolean`

A Boolean value that defines whether the system enables line balancing for the text component.

Default: `false`

`lineHeight`

`integer`

The default line height, in `points`. Apple News recalculates the line height as necessary, relative to the font size. For example, when Apple News automatically resizes the font to fit a smaller screen, it also adjusts the line height accordingly.

`linkStyle`

`(`TextStyle` | string("none"))`

Text styling for all links within a text component.

To remove a previously set condition, use `none`.

Possible types: TextStyle`, ``string("none")`

`orderedListItems`

`(`ListItemStyle` | string("none"))`

An object for use with text components with HTML markup. You can create text styles containing an `orderedListItems` definition to configure how to display list items inside `` tags.

To remove a previously set condition, use `none`.

Possible types: ListItemStyle`, ``string("none")`

`paragraphSpacingAfter`

`integer`

An object that defines the spacing, in points, after each paragraph, relative to the line height.

`paragraphSpacingBefore`

`integer`

An object that defines the spacing, in points, before each paragraph, relative to the line height.

`strikethrough`

`(`TextDecoration` | boolean)`

The text strikethrough. Set `strikethrough` to `true` to use the text color inherited from the `textColor` property as the strikethrough color, or provide a text decoration definition with a different color. By default, Apple News omits `strikethrough` (`false`).

Possible types: TextDecoration`, ``boolean`

`stroke`

`(`TextStrokeStyle` | string("none"))`

The stroke style for the text outline. By default, Apple News omits `stroke`.

To remove a previously set condition, use `none`.

Possible types: TextStrokeStyle`, ``string("none")`

`textAlignment`

`string`

The justification for all text within the component.

If Apple News omits `textAlignment` or sets it to `none`, the justification is determined by the text direction (left-to-right text is aligned to the left, and right-to-left text is aligned to the right).

Default: `none`

Possible Values: `left, center, right, justified, none`

`textColor`

Color

The text color to apply to the selected text.

`textShadow`

`(`TextShadow` | string("none"))`

The text shadow for this style.

To remove a previously set condition, use `none`.

Possible types: TextShadow`, ``string("none")`

`textTransform`

`string`

The transform to apply to the text.

Valid values:

- `uppercase`

- `lowercase`

- `capitalize`. Capitalizes the first letter of all words in the string.

- `smallcaps`. Capitalizes the lowercase letters as short capital letters.

- `none` (default)

Possible Values: `uppercase, lowercase, capitalize, smallcaps, none`

`tracking`

`number`

The amount of tracking (spacing between characters) in text, as a percentage of the font size. The actual spacing between letters is determined by combining information from the font and font size.

Example: Set `tracking` to 0.5 to make the distance between characters increase by 50% of the `fontSize`. With a font size of 10, the additional space between characters is 5 points.

Default: `0`

`underline`

`(`TextDecoration` | boolean)`

The text underlining. You can use this style for links. Set `underline` to `true` to use the text color as the underline color, or provide a text decoration with a different color. By default, Apple News omits underline (`false`).

Possible types: TextDecoration`, ``boolean`

`unorderedListItems`

`(`ListItemStyle` | string("none"))`

An object for use with text components with HTML markup. You can create text styles containing an `unorderedListItems` definition to configure how to display list items inside `` tags.

To remove a previously set condition, use `none`.

Possible types: ListItemStyle`, ``string("none")`

`verticalAlignment`

`string`

The vertical alignment of the text. You can use this property for superscript and subscript.

To override values specified in parent text styles, use `baseline`.

Defaults to `baseline` when unspecified, and inherits the value specified in a `TextStyle` applied to the same range.

The values `superscript` and `subscript` also adjust the font size to 2/3 of the size defined for that character range.

Possible Values: `superscript, subscript, baseline`

## Mentioned in 

Supporting Dark Mode for Your Article

## Discussion

Use the `ConditionalComponentTextStyle` object to define an array of conditional component text style properties and the conditions under which to apply them. When a condition is met, the value of a property in `ConditionalComponentTextStyle` overrides the value of the same property if you define it in the parent `ComponentTextStyle` object. See ComponentTextStyle.

### Example

```
{
  "components": [
    {
      "role": "title",
      "text": "Lorem Ipsum Dolor Sit Amet",
      "textStyle": "exampleTextStyle"
    }
  ],
  "componentTextStyles": {
    "exampleTextStyle": {
      "fontSize": 24,
      "conditional": [
        {
          "fontSize": 24,
          "conditions": [
            {
              "minViewportWidth": 0
            }
          ]
        },
        {
          "fontSize": 48,
          "conditions": [
            {
              "minViewportWidth": 415
            }
          ]
        },
        {
          "fontSize": 64,
          "conditions": [
            {
              "minViewportWidth": 769
            }
          ]
        }
      ]
    }
  }
}
```

## Relationships

### Inherits From

- TextStyle

## See Also

### Conditional Design Elements

object Condition

The object for defining a condition that, when met, causes conditional properties to go into effect.

object ConditionalComponent

The object for defining conditional properties for a component, and when the conditional properties are in effect.

object ConditionalComponentLayout

The object for defining conditional properties for a component layout, and when the conditional properties are in effect.

object ConditionalAutoPlacement

The object for defining conditional properties for an automatically placed component, and when the conditional properties are in effect.

object ConditionalSection

The object for defining conditional properties for a section component, and when the conditional properties are in effect.

object ConditionalDocumentStyle

The object for defining conditional properties for a document style, and when the conditional properties are in effect.

object ConditionalText

The object for defining conditional properties for a text component, and when the conditional properties are in effect.

object ConditionalTextStyle

The object for defining conditional properties for a text style, and when the conditional properties are in effect.

object ConditionalComponentStyle

The object for defining conditional properties for a component style, and when the conditional properties are in effect.

object ConditionalContainer

The object for defining conditional properties for a container component, and when the conditional properties are in effect.

object ConditionalDivider

The object for defining conditional properties for a divider component, and when the conditional properties are in effect.

object ConditionalButton

The object for defining a button component’s conditional properties, and when the conditional properties are in effect.

