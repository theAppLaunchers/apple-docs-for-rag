

- Apple News Format
-  ConditionalComponentStyle 

Object

# ConditionalComponentStyle

The object for defining conditional properties for a component style, and when the conditional properties are in effect.

Apple News Format 1.9+

``` source
object ConditionalComponentStyle
```

## Properties

`conditions`

`(`Condition` | [`Condition`])`

 (Required) 

An instance or array of conditions that, when met, cause the conditional component style properties to take effect.

Possible types: Condition`, ``[`Condition`]`

`backgroundColor`

`(`Color` | string("none"))`

The component’s background color. This value defaults to transparent.

To remove a previously set condition, use `none`.

Possible types: Color`, ``string("none")`

`border`

`(`Border` | string("none"))`

The border for the component. Because the border is inside the component, it affects the size of the content within the component. The bigger the border, the less available space for content.

To remove a previously set condition, use `none`.

Possible types: Border`, ``string("none")`

`fill`

`(`Fill` | string("none"))`

A fill object, such as an ImageFill, that Apple News applies on top of the specified `backgroundColor`.

By default, Apply News doesn’t apply any fill.

To remove a previously set condition, use `none`.

Possible types: Fill`, ``string("none")`

`mask`

`(`CornerMask` | string("none"))`

A mask that clips the contents of the component to the specified masking behavior.

To remove a previously set condition, use `none`.

Possible types: CornerMask`, ``string("none")`

`opacity`

`number`

The opacity of the component, set as a `float` value between `0` (completely transparent) and `1` (completely opaque). All child components inherit the effects of the component’s opacity. See Nesting Components in an Article.

Default: `1`

`tableStyle`

`(`TableStyle` | string("none"))`

The styling for the rows, columns, and cells of the component, if it’s a DataTable or HTMLTable component.

To remove a previously set condition, use `none`.

Possible types: TableStyle`, ``string("none")`

`shadow`

ComponentShadow

The object for creating a component shadow.

## Mentioned in 

Supporting Dark Mode for Your Article

## Discussion

Use the `ConditionalComponentStyle` object to define an array of conditional component style properties and the conditions under which to apply them. When a condition is met, the value of a property in `ConditionalComponentStyle` overrides the value of the same property if you define it in the parent `ComponentStyle` object. See ComponentStyle.

### Example

```
{
  "components": [
    {
      "role": "body",
      "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
      "style": "exampleStyle"
    }
  ],
  "componentStyles": {
    "exampleStyle": {
      "backgroundColor": "#e3e3e3",
      "conditional": [
        {
          "backgroundColor": "goldenrod",
          "conditions": [
            {
              "verticalSizeClass": "compact"
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

- ComponentStyle

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

object ConditionalComponentTextStyle

The object for defining conditional properties for a component text style, and when the conditional properties are in effect.

object ConditionalContainer

The object for defining conditional properties for a container component, and when the conditional properties are in effect.

object ConditionalDivider

The object for defining conditional properties for a divider component, and when the conditional properties are in effect.

object ConditionalButton

The object for defining a button component’s conditional properties, and when the conditional properties are in effect.

