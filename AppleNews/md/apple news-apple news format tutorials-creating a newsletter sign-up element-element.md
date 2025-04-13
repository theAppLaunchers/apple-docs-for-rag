

- Apple News
- Apple News Format Tutorials
-  Creating a Newsletter Sign-Up Element 

Article

# Creating a Newsletter Sign-Up Element

Add a newsletter sign-up element in your article.

## Overview

You can provide your readers the option to sign up for your publication’s newsletter from an article. By using styles and layouts thoughtfully, you can visually separate your newsletter sign-up element from your article content.

**On this page, you’ll learn how to:**

- Add the newsletter sign-up element to your article.

- Use components, component styles, component text styles, and layout objects to customize the display of the newsletter sign-up element.

### Create Component Layout Objects for Newsletter Sign-Up

To make adjustments to the positioning of the newsletter sign-up element, you must first create new `ComponentLayout` objects:

1.  Copy the example code Layout: Copy This Code.

2.  Paste the code between the closing brace (`}`) of the last `componentLayout` object and the closing brace for the whole `ComponentLayouts` property.

Your code should look like the example code Layout: Result.

#### Layout: Copy This Code

```
,
     "newsletterLayout": {
       "padding": 30
     },
     "newsletterHeadingLayout": {
       "margin": {
         "bottom": 24
       }
     },
     "newsletterBodyLayout": {
       "margin": {
         "bottom": 26
       }
     },
     "newsletterButtonLayout": {
       "padding": {
         "left": 24,
         "right": 24,
         "top": 12,
         "bottom": 12
       }
     }
```

#### Layout: Result

Ellipses (…) indicate lines of code are omitted from this example.

```
{
  ...
  "componentLayouts": {
    ...
    "newsletterLayout": {
      "padding": 30
    },
    "newsletterHeadingLayout": {
      "margin": {
         "bottom": 24
      }
    },
    "newsletterBodyLayout": {
      "margin": {
         "bottom": 26
      }
    },
    "newsletterButtonLayout": {
      "padding": {
         "left": 24,
         "right": 24,
         "top": 12,
         "bottom": 12
      }
    }
  },
  ...
}
```

### Define Component Styles for the Newsletter Sign-Up Element

Create a new `ComponentStyles` object so that you can apply styles to the newsletter sign-up element.

1.  Copy the example code Component Styles: Copy This Code.

2.  Paste the code between after the `backgroundColor` property of the `sidebarBackgroundStyle` object and the closing brace (`}`) for the whole `componentStyles` property.

Your code should look like the example code Component Styles: Result.

#### Component Styles: Copy This Code

```
,
 "newsletterStyle": {
      "mask": {
        "type": "corners",
        "radius": 6
      },
      "backgroundColor": "#F8F8FA",
      "conditional": [
        {
          "backgroundColor": "#1C1C1E",
          "conditions": [
            {
              "preferredColorScheme": "dark"
            }
          ]
        }
      ]
    },
    "newsletterButtonStyle": {
      "border": {
        "all": {
          "color": "#000000",
          "width": 1
        }
      },
      "mask": {
        "type": "corners",
        "radius": 6
      }
    }
```

#### Component Styles: Result

Ellipses (…) indicate lines of code that are omitted from this example.

```
{
  ...
  "componentStyles": {
    ...
    "newsletterStyle": {
      "mask": {
        "type": "corners",
        "radius": 6
      },
      "backgroundColor": "#F8F8FA",
      "conditional": [
        {
          "backgroundColor": "#1C1C1E",
          "conditions": [
            {
              "preferredColorScheme": "dark"
            }
          ]
        }
      ]
    },
    "newsletterButtonStyle": {
      "border": {
        "all": {
          "color": "#000000",
          "width": 1
        }
      },
      "mask": {
        "type": "corners",
        "radius": 6
      }
    }
  },
  ...
},
```

### Define Component Text Styles for the Newsletter Sign-Up Element

Create new `ComponentTextStyle` objects so that you can apply text styles to the heading, body, and button for the newsletter sign-up element.

1.  Copy the example code Component Text Styles: Copy This Code.

2.  Paste the code after the last `componentTextStyle` object and the closing brace (}) for the whole `componentTextStyles` object.

Your code should look like the example code Component Text Styles: Result.

#### Component Text Styles: Copy This Code

```
,
 "newsletterHeadingTextStyle": {
      "fontName": "HelveticaNeue",
      "fontSize": 20,
      "textColor": "#000000",
      "textAlignment": "center"
    },
    "newsletterBodyTextStyle": {
      "fontName": "HelveticaNeue",
      "fontSize": 15,
      "lineHeight": 18,
      "textColor": "#000000",
      "textAlignment": "center"
    },
    "newsletterButtonTextStyle": {
      "fontName": "HelveticaNeue",
      "fontSize": 15,
      "textColor": "#000000",
      "textAlignment": "center"
   }
```

#### Component Text Styles: Result

Ellipses (…) indicate lines of code that are omitted from this example.

```
{
  ...
  "componentTextStyles": {
    ...
    "newsletterHeadingTextStyle": {
      "fontName": "HelveticaNeue",
      "fontSize": 20,
      "textColor": "#000000",
      "textAlignment": "center"
    },
    "newsletterBodyTextStyle": {
      "fontName": "HelveticaNeue",
      "fontSize": 15,
      "lineHeight": 18,
      "textColor": "#000000",
      "textAlignment": "center"
    },
    "newsletterButtonTextStyle": {
      "fontName": "HelveticaNeue",
      "fontSize": 15,
      "textColor": "#000000",
      "textAlignment": "center"
    }
  }
}
```

### Add a Newsletter Sign-Up Element in your Article

Finally, add the newsletter sign-up element to your article.

1.  Copy the example code Newsletter: Copy This Code.

2.  Paste the code after the Twitter URL and before the closing square bracket (\]) at the end of the `components` array.

Your code should look like the example code in Newsletter: Result.

#### Newsletter: Copy This Code

```
 ,
  {
          "role": "heading2",
          "layout": "fullMarginAboveHalfBelowLayout",
          "text": "NEWSLETTER SIGN-UP"
        },
        {
          "role": "body",
          "format": "html",
          "layout": "noMarginLayout",
          "text": "Sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas."
        },
        {
          "role": "container",
          "layout": "newsletterLayout",
          "style": "newsletterStyle",
          "components": [
            {
              "role": "heading3",
              "text": "Lorem ipsum dolor sit amet",
              "textStyle": "newsletterHeadingTextStyle",
              "layout": "newsletterHeadingLayout"
            },
            {
              "role": "body",
              "text": "Sign up for our daily newsletter, delivered straight to your inbox.",
              "textStyle": "newsletterBodyTextStyle",
              "layout": "newsletterBodyLayout"
            },
            {
              "role": "link_button",
              "format": "html",
              "URL": "https://apple.com",
              "text": "Sign Up &#x2197;&#xFE0E;",
              "textStyle": "newsletterButtonTextStyle",
              "layout": "newsletterButtonLayout",
              "style": "newsletterButtonStyle"
            }
          ]
        }
```

#### Newsletter: Result

Ellipses (…) indicate lines of code that are omitted from this example.

```
{
  ...
  "components": [
    ...
        {
          "role": "heading2",
          "layout": "fullMarginAboveHalfBelowLayout",
          "text": "NEWSLETTER SIGN-UP"
        },
        {
          "role": "body",
          "format": "html",
          "layout": "noMarginLayout",
          "text": "Sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas."
        },
        {
          "role": "container",
          "layout": "newsletterLayout",
          "style": "newsletterStyle",
          "components": [
            {
              "role": "heading3",
              "text": "Lorem ipsum dolor sit amet",
              "textStyle": "newsletterHeadingTextStyle",
              "layout": "newsletterHeadingLayout"
            },
            {
              "role": "body",
              "text": "Sign up for our daily newsletter, delivered straight to your inbox.",
              "textStyle": "newsletterBodyTextStyle",
              "layout": "newsletterBodyLayout"
            },
            {
              "role": "link_button",
              "format": "html",
              "URL": "https://apple.com",
              "text": "Sign Up &#x2197;&#xFE0E;",
              "textStyle": "newsletterButtonTextStyle",
              "layout": "newsletterButtonLayout",
              "style": "newsletterButtonStyle"
            }
          ]
        }
      ]
    }
  ],
  ...
}
```

### Previous

Adding a Fixed Image Fill

### Next

Viewing the Finished Article for Advanced Design Tutorial 3

## See Also

### Advanced Design Tutorial 3: More Ideas

Giving the Article a Dark Color Scheme

Apply a new color scheme to your article.

Adding a Video

Add a video component inside the header component.

Creating a Sidebar

Create a box with an HTML bulleted list in the margin.

Adding a Fixed Image Fill

Add an image that remains stationary when the user scrolls.

Viewing the Finished Article for Advanced Design Tutorial 3

See the full JSON code from this tutorial.

