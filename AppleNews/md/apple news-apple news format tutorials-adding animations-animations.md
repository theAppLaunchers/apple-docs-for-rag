

- Apple News
- Apple News Format Tutorials
-  Adding Animations 

Article

# Adding Animations

Use animations to affect how parts of your article come into view the first time they appear.

## Overview

**On this page, you’ll learn how to apply animations to components.**

The images below display some animations. In the first image, the pull quote gets larger and darker as the user scrolls through the text. In the second image, the photo gets darker, but not larger, as the user scrolls. In the third image, the gallery moves in from the right side of the screen.

### Create Animations

1.  Copy the example code Scale Fade Animation: Copy This Code.

2.  Paste the code inside the `pullquote` component in your `article.json` file, after the closing quotation mark that ends the `text` property.

3.  Copy the example code Move-In Animation: Copy This Code.

4.  Paste the code inside the `gallery` component in your `article.json` file, after the comma that ends the `layout` property.

5.  Copy the example code Fade-In Animation: Copy This Code.

6.  Paste the code inside the `photo` component in your `article.json` file, after the closing quotation mark that ends the `caption` property.

Your code should look like the example code Animations: Result.

After you make these changes in your code, you can preview your working `article.json` file in News Preview to see the animations.

#### Scale Fade Animation: Copy This Code

```
,
              "animation": {
                "type": "scale_fade",
                "userControllable": true,
                "initialAlpha": 0.5,
                "initialScale": 0.75
              }
```

#### Move-In Animation: Copy This Code

```
          "animation": {
            "type": "move_in",
            "preferredStartingPosition": "right"
          },
```

#### Fade-In Animation: Copy This Code

```
,
              "animation": {
                "type": "fade_in",
                "userControllable": true,
                "initialAlpha": 0.5
              }
```

#### Animations: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "components": [
    ...
    {
      "role": "section",
      ...
      "components": [
        ...
        {
          "role": "container",
          ...
          "components": [
            {
              "role": "pullquote",
              "format": "html",
              "layout": "halfMarginAboveQuarterBelowContainedLayout",
              "text": "“QUIA CONSEQUUNTUR MAGNI DOLORES EOS QUI RATIONE VOLUPTATEM SEQUI NESCIUNT.”",
              "animation": {
                "type": "scale_fade",
                "userControllable": true,
                "initialAlpha": 0.5,
                "initialScale": 0.75
              }
            },
            ...
          ]
        },
        ...
        {
          "role": "gallery",
          "layout": "noMarginLayout",
          "animation": {
            "type": "move_in",
            "preferredStartingPosition": "right"
          },
          "items": [
            ...
          ]
        },
        ...
        {
          "role": "container",
          ...
          "components": [
            {
              "role": "photo",
              "layout": "halfMarginAboveContainedLayout",
              "URL": "bundle://sidebar.jpg",
              "caption": "A caption for the sidebar photo.",
              "animation": {
                "type": "fade_in",
                "userControllable": true,
                "initialAlpha": 0.5
              }
            },
            ...
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

Adding Color to Text Ranges

### Next

Adding a Scene

## See Also

### Related Documentation

About Component Animations

Learn how to affect the way in which components come into view.

### Advanced Design Tutorial 2: Layout and Positioning

Creating a Complex, Layered Header

Layer a title and heading in front of an image, with their colors optimized for legibility.

Creating a Floating Caption

Position a caption in the wide right margin of your article.

Creating an Inset Pull Quote

Wrap article body text around an inset pull quote.

Creating an Inset Photo

Wrap article body text around an inset photo.

Adding Color to Text Ranges

Create text in color by using HTML to refer to TextStyle objects.

Adding a Scene

Control how the article’s opening section comes into view.

Viewing the Finished Article for Advanced Design Tutorial 2

See the full JSON code from this tutorial.

