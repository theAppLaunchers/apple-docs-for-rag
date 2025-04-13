

- Apple News
- Apple News Format Tutorials
-  Adding a Divider 

Article

# Adding a Divider

Create a horizontal, styled divider that extends to the right edge of the display.

## Overview

In Creating Your First Article, you added some text components to your article. Now, you can add a `divider` component to visually separate some text components and create color contrast.

**On this page, you’ll learn how to create a horizontal dividing line that extends to the right edge of the display.**

### Define a ComponentLayout Object that Bleeds to the Right Edge

Before you can make your divider line extend to the right edge of the display, you must define a new `ComponentLayout` object that uses the `ignoreDocumentMargin` property.

1.  Copy the example code bigDividerLayout: Copy This Code.

2.  Paste the code inside your `ArticleDocument.componentLayouts` object, after the closing brace (`}`) of the last `ComponentLayout` object and before the closing brace for the whole `componentLayouts` property.

Your code should look like the example code bigDividerLayout: Result.

#### bigDividerLayout: Copy This Code

```
,
    "bigDividerLayout": {
      "ignoreDocumentMargin": "right",
      "columnStart": 0,
      "columnSpan": 20,
      "margin": {
        "top": 6,
        "bottom": 6
      }
    }
```

#### bigDividerLayout: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "componentLayouts": {
    ...
    "bigDividerLayout": {
      "ignoreDocumentMargin": "right",
      "columnStart": 0,
      "columnSpan": 20,
      "margin": {
        "top": 6,
        "bottom": 6
      }
    }
  },
  ...
}
```

### Add a Divider in Your Article

A `divider` component in your JSON file represents a divider line in your article.

1.  Copy the example code Divider: Copy This Code.

2.  Paste the code inside the `components` array of your article, after the closing brace and comma (`},`) that end `heading1` component.

Your code should look like the example code Divider: Result.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see a yellow divider.

#### Divider: Copy This Code

```
    {
      "role": "divider",
      "layout": "bigDividerLayout",
      "stroke": {
        "width": 3,
        "color": "#D5B327"
      }
    },
```

#### Divider: Result

Ellipses (…) indicate lines of code that have been omitted from this example.

```
{
  ...
  "components": [
    ...
    {
      "role": "divider",
      "layout": "bigDividerLayout",
      "stroke": {
        "width": 3,
        "color": "#D5B327"
      }
    },
    ...
  ],
  ...
}
```

### Further Exploration

At any time, you can try changing property values in your `article.json` file and then use News Preview to see how these changes affect the look of your article.

For example, try changing the layout of your article’s `divider` component:

1.  In your `article.json` file, find the `ComponentLayout` object called `bigDividerLayout`.

2.  In `bigDividerLayout`, find the `ignoreDocumentMargin` property and replace its value (`"right"`) with `"both"`.

3.  Preview your `article.json` file in News Preview.

The divider now ignores the margins on both sides of the document.

### Previous

Positioning Text Components

### Next

Adding an Image and Captions

## See Also

### Related Documentation

object Divider

The component for defining a horizontal line to visually divide parts of your article.

object ComponentLayout

The object for defining the positioning for a specific component within the article’s column system.

object StrokeStyle

The object for defining the color, width, and style of a border or divider.

### Introductory Design Tutorial

Setting Up the Introductory Tutorial

Download the tutorial files, and learn about what you’ll create in the introductory tutorial.

Creating Your First Article

Create an article with text components and component text styles.

Positioning Text Components

Adjust the positions of the text components in your article—for example, place the article body off-center.

Adding an Image and Captions

Create a photo that extends to both edges of the display, with captions that appear in the article layout and in full-screen view.

Adding a Pull Quote

Break an existing body component into two components, and then insert a pull quote between them.

Adding a Gallery of Images

Display three images as a sequential gallery.

Adding a Mosaic of Images

Display five images as mosaic tiles.

Adding a Tweet

Include a tweet in an article.

Adding a Podcast

Add a link to a podcast that displays the podcast artwork and the podcast show or episode information.

Viewing the Finished Article for the Introductory Design Tutorial

See the full JSON code from this tutorial.

