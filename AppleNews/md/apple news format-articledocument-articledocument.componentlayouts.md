

- Apple News Format
- ArticleDocument
-  ArticleDocument.componentLayouts 

Object

# ArticleDocument.componentLayouts

An object containing component layout objects that components in the article can refer to.

Apple News Format 1.7+

``` source
object ArticleDocument.componentLayouts
```

## Properties

`Any Key`

ComponentLayout

A component layout, with a name you define that components within this document can refer to.

## Mentioned in 

Positioning the Content in Your Article

## Discussion

`ArticleDocument.componentLayouts` is an object containing the component layout objects that components in your article can use. You provide each component layout object as a key-value pair. In each pair, you create a key that’s meaningful to you. The value of each pair is a ComponentLayout object.

### Example

```
{
  "title": "Sample Article",
  "identifier": "sample",
  "version": "1.8",
  "language": "en",
  "layout": {
    "columns": 20,
    "width": 1024,
    "margin": 60,
    "gutter": 20
  },
  "documentStyle": {
    "backgroundColor": "#F7F7F7"
  },
  "components": [
    {
      "role": "body",
      "format": "html",
      "layout": "exampleLayout",
      "text": "There is a moment in every dawn when light floats, there is the possibility of magic."
    }
  ],
  "componentTextStyles": {},
  "textStyles": {},
  "componentStyles": {},
  "componentLayouts": {
    "exampleLayout": {
      "columnStart": 0,
      "columnSpan": 3,
      "margin": {
        "top": 50,
        "bottom": 50
      }
    }
  }
}
```

## See Also

### Objects

object ArticleDocument.componentStyles

An object containing component style objects that components in the article can refer to.

object ArticleDocument.componentTextStyles

An object containing component text style defaults as well as component text styles that components in the article can use.

object ArticleDocument.textStyles

An object containing text style objects that components within this document can refer to inline in text.

object ArticleDocument.colorScheme

The object that contains information about the color scheme of the document, including Dark Mode behavior.

