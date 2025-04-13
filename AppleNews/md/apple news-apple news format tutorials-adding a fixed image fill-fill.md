

- Apple News
- Apple News Format Tutorials
-  Adding a Fixed Image Fill 

Article

# Adding a Fixed Image Fill

Add an image that remains stationary when the user scrolls.

## Overview

The fixed image fill is one of the most captivating effects in Apple News Format. A fixed image fill stays still when the user scrolls. As long as any portion of the filled component is visible in the viewport, the image maintains one position, while the rest of the article seems to scroll independently of the image.

**On this page, you’ll learn how to use the fixed image fill.**

### Create a ComponentLayout Object for the Fixed Image

Before you can make the image span the whole display area, you must create a new `ComponentLayout` object.

1.  Copy the example code fullScreenImageLayout: Copy This Code.

2.  Paste the code between the closing brace (`}`) of the last `ComponentLayout` object and the closing brace for the whole `componentLayouts` property.

Your code should look like the example code fullScreenImageLayout: Result.

#### fullScreenImageLayout: Copy This Code

```
,
    "fullScreenImageLayout": {
      "ignoreDocumentMargin": true,
      "minimumHeight": "100vmax",
      "margin": {
        "top": 24,
        "bottom": 12
      }
    }
```

#### fullScreenImageLayout: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "componentLayouts": {
    ...
    "fullScreenImageLayout": {
      "ignoreDocumentMargin": true,
      "minimumHeight": "100vmax",
      "margin": {
        "top": 24,
        "bottom": 12
      }
    }
  },
...
}
```

### Create a ComponentTextStyle Object for the Pull Quote

Create a new `ComponentTextStyle` object for a new color.

1.  Copy the example code pullquoteLight: Copy This Code.

2.  Paste the code between the closing brace (`}`) of the last `ComponentTextStyle` object and the closing brace for the whole `componentTextStyles` property.

Your code should look like the example code pullquoteLight: Result.

#### pullquoteLight: Copy This Code

```
,
    "pullquoteLight": {
      "textColor": "#F5F9FB"
    }
```

#### pullquoteLight: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "componentTextStyles": {
    ...
    "pullquoteLight": {
      "textColor": "#F5F9FB"
    }
  }
...
}
```

### Add a New Container with a Fixed Image Fill

In Download the Article Bundle Examples, you downloaded a bundle called `News_Design_Tutorial_Advanced_Article_3` that contains a thumbnail image. Now, you’ll move that image into your working folder and use it as an image fill.

1.  Move the `static-background.jpg` file from the `News_Design_Tutorial_Advanced_Article_3` folder to the folder that contains your working `article.json` file.

2.  Copy the example code Fixed Image Fill: Copy This Code.

3.  Paste the code inside your second section, near the end, before this code: `{ "role": tweet,`

Your code should look like the example code Fixed Image Fill: Result.

#### Fixed Image Fill: Copy This Code

```
        {
          "role": "container",
          "layout": "fullScreenImageLayout",
          "style": {
            "fill": {
              "type": "image",
              "URL": "bundle://static-background.jpg",
              "fillMode": "cover",
              "attachment": "fixed",
              "verticalAlignment": "center",
              "horizontalAlignment": "center"
            }
          },
          "components": [
            {
              "role": "pullquote",
              "layout": "fullMarginBelowLayout",
              "textStyle": "pullquoteLight",
              "text": "“QUIA CONSEQUUNTUR MAGNI DOLORES EOS QUI RATIONE VOLUPTATEM SEQUI NESCIUNT.”",
              "anchor": {
                "targetAnchorPosition": "center"
              }
            }
          ]
        },
```

#### Fixed Image Fill: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "components": [
    ...
    {
      "role": "section",
      "layout": "fullBleedLayout",
      "style": "bodyBackgroundStyle",
      "components": [
        ...
        {
          "role": "container",
          "layout": "fullScreenImageLayout",
          "style": {
            "fill": {
              "type": "image",
              "URL": "bundle://static-background.jpg",
              "fillMode": "cover",
              "attachment": "fixed",
              "verticalAlignment": "center",
              "horizontalAlignment": "center"
            }
          },
          "components": [
            {
              "role": "pullquote",
              "layout": "fullMarginBelowLayout",
              "textStyle": "pullquoteLight",
              "text": "“QUIA CONSEQUUNTUR MAGNI DOLORES EOS QUI RATIONE VOLUPTATEM SEQUI NESCIUNT.”",
              "anchor": {
                "targetAnchorPosition": "center"
              }
            }
          ]
        },
        ...
      ]
    }
  ],
  ...
}
```

### Previous

Creating a Sidebar

### Next

Creating a Newsletter Sign-Up Element

## See Also

### Related Documentation

object ImageFill

The object for adding an image background fill to a component.

Specifying Measurements for Components

Specify the units of measure to use for margins, minimum heights, and other dimensions.

### Advanced Design Tutorial 3: More Ideas

Giving the Article a Dark Color Scheme

Apply a new color scheme to your article.

Adding a Video

Add a video component inside the header component.

Creating a Sidebar

Create a box with an HTML bulleted list in the margin.

Creating a Newsletter Sign-Up Element

Add a newsletter sign-up element in your article.

Viewing the Finished Article for Advanced Design Tutorial 3

See the full JSON code from this tutorial.

