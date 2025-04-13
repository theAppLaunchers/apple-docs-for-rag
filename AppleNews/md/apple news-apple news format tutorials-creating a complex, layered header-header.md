

- Apple News
- Apple News Format Tutorials
-  Creating a Complex, Layered Header 

Article

# Creating a Complex, Layered Header

Layer a title and heading in front of an image, with their colors optimized for legibility.

## Overview

In the first advanced tutorial, you created a header with layering and parallax behavior.

In this second article, you’ll add more code to the same article to modify the layout. You’ll wrap body text around an image, place captions in the article margin, create a more complex header, and add component animations.

**On this page, you’ll learn how to create a more complex layered header.**

### Move Title and Heading Text into the Header

First, you need to layer title and heading information in front of the header’s image fill. You’ll move `heading1`, `divider`, and `title` components from the second section of the article into the `header` component.

This image shows the heading and title before they have been lightened for legibility; you’ll lighten this text in Define a Light Text Style for Heading Text.

1.  Open the `article.json` file that you completed in Adding Parallax Behavior, or open `Desktop/News_Design_Tutorial/News_Design_Tutorial_Advanced_Article_1/article.json`.

2.  In the `article.json` file (not the example code below), cut the first three components inside the second section to your clipboard. The code you are cutting begins with the opening bracket (`{`) before `"role": "heading1",` and ends with the closing bracket and comma (`},`) that end the `title` component.

3.  Paste the components inside the `components` array in your article’s header, after the opening square bracket (`[`) that comes a few lines after this line: `"role": "header",`

Your code should look like the example code Moving Components: Result.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see that the title is layered in front of the header as shown in the previous figure.

#### Moving Components: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "components": [
    {
      "role": "section",
      "layout": "fullBleedLayout",
      "behavior": {
        "type": "parallax",
        "factor": 0.8
      },
      "components": [
        {
          "role": "header",
          "layout": "headerImageLayout",
          "style": {
            "fill": {
              "type": "image",
              "URL": "bundle://header.jpg",
              "fillMode": "cover",
              "verticalAlignment": "top",
              "horizontalAlignment": "center"
            }
          },
          "components": [
            {
              "role": "heading1",
              "layout": "heading1Layout",
              "text": "HEADING"
            },
            {
              "role": "divider",
              "layout": "bigDividerLayout",
              "stroke": {
                "width": 3,
                "color": "#D5B327"
              }
            },
            {
              "role": "title",
              "layout": "halfMarginBelowLayout",
              "text": "ARTICLE TITLE"
            },
            {
              "role": "container",
              "layout": "fullBleedLayout",
              "style": "captionBarBackgroundStyle",
              "anchor": {
                "targetAnchorPosition": "bottom"
              },
              "components": [
                {
                  "role": "caption",
                  "textStyle": "captionLight",
                  "layout": "halfMarginBothLayout",
                  "text": "ABOVE: Sed ut pers piciatis unde omnis iste error sit volup tatem accusantium dolor emque, totam rem. (Attribution)"
                }
              ]
            }
          ]
        }
      ]
    },
    ...
  ],
  ...
}
```

### Create More Space Above the Intro Component

When you moved your title in Move Title and Heading Text into the Header, the spacing around your `intro` component changed. You can use an already defined `ComponentLayout` object to create more space above the `intro` component.

To create additional space, in your `article.json` file, inside the `intro` component, change the value of `layout` from `"halfMarginBelowLayout"` to `"halfMarginBothLayout"`.

Your code should look like the example code Intro ComponentLayout Object: Result.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see the adjustment to the `intro` component’s position.

#### Intro ComponentLayout Object: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "components": [
    {
      "role": "section",
      "layout": "fullBleedLayout",
      "behavior": {
        "type": "parallax",
        "factor": 0.8
      },
      "components": [
        ...
      ]
    },
    {
      "role": "section",
      "layout": "fullBleedLayout",
      "style": "bodyBackgroundStyle",
      "components": [
        {
          "role": "intro",
          "layout": "halfMarginBothLayout",
          "text": "Etiam rhoncus. Maecenas tempus, tellus eget condimentum rhoncus, sem quam semper libero, sit amet adipiscing sem neque ipsum?"
        },
        ...
      ]
    }
  ],
  ...
}
```

### Anchor the Title to the Bottom of the Header

If you anchor multiple child components to the same side of the parent, the children will stack as in the following figure. This image shows the heading and title before they have been lightened for legibility; you’ll lighten this text in Use the Dark Background and Light Text.

1.  In your working `article.json` file, delete the contents of the `components` array inside your `header` component.

2.  Copy the example code Header Contents: Copy This Code.

3.  Paste the code inside the now-empty `components` array of the header, where you deleted content in step 1. Make sure to paste inside the square brackets (`[]`).

Your code should look like the example code Header Contents: Result.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see that the article title information is anchored to the bottom of the header.

#### Header Contents: Copy This Code

```
            {
              "role": "container",
              "layout": "fullBleedLayout",
              "anchor": {
                "targetAnchorPosition": "bottom"
              },
              "components": [
                {
                  "role": "heading1",
                  "layout": "heading1Layout",
                  "text": "HEADING"
                },
                {
                  "role": "divider",
                  "layout": "bigDividerLayout",
                  "stroke": {
                    "width": 3,
                    "color": "#D5B327"
                  }
                },
                {
                  "role": "title",
                  "format": "html",
                  "layout": "halfMarginBelowLayout",
                  "text": "ARTICLE TITLE"
                }
              ]
            },
            {
              "role": "container",
              "layout": "fullBleedLayout",
              "style": "captionBarBackgroundStyle",
              "anchor": {
                "targetAnchorPosition": "bottom"
              },
              "components": [
                {
                  "role": "caption",
                  "textStyle": "captionLight",
                  "layout": "halfMarginBothLayout",
                  "text": "ABOVE: Sed ut pers piciatis unde omnis iste error sit volup tatem accusantium dolor emque, totam rem. (Attribution)"
                }
              ]
            }
```

#### Header Contents: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "components": [
    {
      "role": "section",
      "layout": "fullBleedLayout",
      "behavior": {
        "type": "parallax",
        "factor": 0.8
      },
      "components": [
        {
          "role": "header",
          "layout": "headerImageLayout",
          "style": {
            "fill": {
              "type": "image",
              "URL": "bundle://header.jpg",
              "fillMode": "cover",
              "verticalAlignment": "top",
              "horizontalAlignment": "center"
            }
          },
          "components": [
            {
              "role": "container",
              "layout": "fullBleedLayout",
              "anchor": {
                "targetAnchorPosition": "bottom"
              },
              "components": [
                {
                  "role": "heading1",
                  "layout": "heading1Layout",
                  "text": "HEADING"
                },
                {
                  "role": "divider",
                  "layout": "bigDividerLayout",
                  "stroke": {
                    "width": 3,
                    "color": "#D5B327"
                  }
                },
                {
                  "role": "title",
                  "format": "html",
                  "layout": "halfMarginBelowLayout",
                  "text": "ARTICLE TITLE"
                }
              ]
            },
            {
              "role": "container",
              "layout": "fullBleedLayout",
              "style": "captionBarBackgroundStyle",
              "anchor": {
                "targetAnchorPosition": "bottom"
              },
              "components": [
                {
                  "role": "caption",
                  "textStyle": "captionLight",
                  "layout": "halfMarginBothLayout",
                  "text": "ABOVE: Sed ut pers piciatis unde omnis iste error sit volup tatem accusantium dolor emque, totam rem. (Attribution)"
                }
              ]
            }
          ]
        }
      ]
    },
    ...
  ],
  ...
}
```

### Define a Dark Background for the Title and Heading

To add contrast to your title and heading text, you can adjust the text color and the background of the text’s parent container. You’ll set the title container background to a gradient that fades from transparent at the top to black at the bottom.

1.  Copy the example code scrimBackgroundStyle: Copy This Code.

2.  Paste the code between the closing brace (`}`) of the last `ComponentStyle` object and the closing brace for the whole `componentStyles` property.

Your code should look like the example code scrimBackgroundStyle: Result.

#### scrimBackgroundStyle: Copy This Code

```
,
    "scrimBackgroundStyle": {
      "fill": {
        "type": "linear_gradient",
        "colorStops": [
          {
            "color": "#00000000"
          },
          {
            "color": "#00000090"
          }
        ]
      }
    }
```

#### scrimBackgroundStyle: Result

```
{
  ...
  "componentStyles": {
    ...
    "scrimBackgroundStyle": {
      "fill": {
        "type": "linear_gradient",
        "colorStops": [
          {
            "color": "#00000000"
          },
          {
            "color": "#00000090"
          }
        ]
      }
    }
  },
  ...
}
```

### Define a Light Text Style for Heading Text

Before you can lighten the text of the heading, you must define a new `ComponentTextStyle` object.

1.  Copy the example code heading1Light: Copy This Code.

2.  Paste the code inside the `ArticleDocument.componentTextStyles` object in your `article.json` file, after the closing brace (`}`) of the last `ComponentTextStyle` object and before the closing brace for the whole `componentTextStyles` property.

Your code should look like the example code heading1Light: Result.

#### heading1Light: Copy This Code

```
,
    "heading1Light": {
      "textColor": "#FFF"
    }
```

#### heading1Light: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "componentTextStyles": {
    ...
    "heading1Light": {
      "textColor": "#FFF"
    }
  }
  ...
}

```

### Use the Dark Background and Light Text

Now you can add references to the `scrimBackgroundStyle` and `heading1Light` objects.

1.  In your `article.json` file, inside the `header` component’s child container, add a property named `style` with a value of `"scrimBackgroundStyle"`, as in the example code Dark Background and Light Text: Result.

2.  In your `article.json file`, inside both the `heading1` component and the `title` component, add a property named `textStyle` with a value of `"heading1Light"`, as in the example code Dark Background and Light Text: Result.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see the optimized styling of your header.

#### Dark Background and Light Text: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "components": [
    {
      "role": "section",
      ...
      "components": [
        {
          "role": "header",
          ...
          },
          "components": [
            {
              "role": "container",
              "layout": "fullBleedLayout",
              "style": "scrimBackgroundStyle",
              "anchor": {
                "targetAnchorPosition": "bottom"
              },
              "components": [
                {
                  "role": "heading1",
                  "textStyle": "heading1Light",
                  "layout": "heading1Layout",
                  "text": "HEADING"
                },
                {
                  "role": "divider",
                  "layout": "bigDividerLayout",
                  "stroke": {
                    "width": 3,
                    "color": "#D5B327"
                  }
                },
                {
                  "role": "title",
                  "textStyle": "heading1Light",
                  "format": "html",
                  "layout": "halfMarginBelowLayout",
                  "text": "ARTICLE TITLE"
                }
              ]
            },
            ...
          ]
        }
      ]
    },
    ...
  ],
  ...
}
```

### Previous

Viewing the Finished Article for Advanced Design Tutorial 1

### Next

Creating a Floating Caption

## See Also

### Related Documentation

Positioning the Content in Your Article

Align article components with columns in your layout.

Nesting Components in an Article

Use container components to create the component hierarchies you need for special article designs.

Applying a Background to a Component

Change the appearance of the backgrounds in your article.

Defining and Applying Text Styles

Define and apply custom, default, and inline text styles, or use HTML tags or Markdown syntax to style your text.

object Header

The component for defining the top area of an article, chapter, or section.

object LinearGradientFill

The object for displaying a linear gradient as a component background.

object ComponentLayout

The object for defining the positioning for a specific component within the article’s column system.

object ComponentTextStyle

The object for defining the style for a text component, including spacing, alignment, and drop caps.

object ComponentStyle

The object for setting style properties for components, including background color and fill, borders, and table styles.

### Advanced Design Tutorial 2: Layout and Positioning

Creating a Floating Caption

Position a caption in the wide right margin of your article.

Creating an Inset Pull Quote

Wrap article body text around an inset pull quote.

Creating an Inset Photo

Wrap article body text around an inset photo.

Adding Color to Text Ranges

Create text in color by using HTML to refer to TextStyle objects.

Adding Animations

Use animations to affect how parts of your article come into view the first time they appear.

Adding a Scene

Control how the article’s opening section comes into view.

Viewing the Finished Article for Advanced Design Tutorial 2

See the full JSON code from this tutorial.

