

- Apple News
- Apple News Format Tutorials
-  Adding a Mosaic of Images 

Article

# Adding a Mosaic of Images

Display five images as mosaic tiles.

## Overview

A mosaic lets you display images as part of a larger collection.

**On this page, you’ll learn how to use a mosaic to display images as a set of tiles.**

### Add a Mosaic with Captions in Your Article

In Download the Article Bundle Examples, you downloaded a bundle called `News_Design_Tutorial_5_Galleries` that contains gallery images and mosaic images. Now, you’ll move some of those images into your working folder and create a `mosaic` component to display the images.

In Positioning Text Components and Adding an Image and Captions, you created some `ComponentLayout` objects. You’ll refer to those `ComponentLayout` objects in this code.

1.  Move the `mosaic-01.jpg`, `mosaic-02.jpg`, `mosaic-03.jpg`, `mosaic-04.jpg`, and `mosaic-05.jpg` files from the `Desktop/News_Design/Tutorial/News_Design_Tutorial_5_Galleries` folder that you downloaded in Download the Article Bundle Examples to the folder that contains your working `article.json` file.

2.  Copy example code Mosaic: Copy This Code.

3.  Paste the code inside the `components` array of your article, after the closing brace and comma (`},`) that end the `body` component whose `text` begins with `Et harum quidem`.

Your code should look like the example code Mosaic: Result.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see a mosaic in your article.

#### Mosaic: Copy This Code

```
   {
      "role": "heading2",
      "layout": "fullMarginAboveHalfBelowLayout",
      "text": "MOSAIC HEADING"
    },
    {
      "role": "mosaic",
      "layout": "noMarginLayout",
      "items": [
        {
          "URL": "bundle://mosaic-01.jpg",
          "caption": "A caption for the first image in the mosaic."
        },
        {
          "URL": "bundle://mosaic-02.jpg",
          "caption": "A caption for the second image in the mosaic."
        },
        {
          "URL": "bundle://mosaic-03.jpg",
          "caption": "A caption for the third image in the mosaic."
        },
        {
          "URL": "bundle://mosaic-04.jpg",
          "caption": "A caption for the fourth image in the mosaic."
        },
        {
          "URL": "bundle://mosaic-05.jpg",
          "caption": "A caption for the fifth image in the mosaic."
        }
      ]
    },
    {
      "role": "caption",
      "layout": "halfMarginBothLayout",
      "text": "ABOVE: A caption for the entire mosaic. Individual photos in the mosaic also have their own captions. (Shared attribution)"
    },
    {
      "role": "divider",
      "layout": "noMarginLayout",
      "stroke": {
        "width": 1,
        "color": "#D5B327"
      }
    },
```

#### Mosaic: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "components": [
    ...
    {
      "role": "heading2",
      "layout": "fullMarginAboveHalfBelowLayout",
      "text": "MOSAIC HEADING"
    },
    {
      "role": "mosaic",
      "layout": "noMarginLayout",
      "items": [
        {
          "URL": "bundle://mosaic-01.jpg",
          "caption": "A caption for the first image in the mosaic."
        },
        {
          "URL": "bundle://mosaic-02.jpg",
          "caption": "A caption for the second image in the mosaic."
        },
        {
          "URL": "bundle://mosaic-03.jpg",
          "caption": "A caption for the third image in the mosaic."
        },
        {
          "URL": "bundle://mosaic-04.jpg",
          "caption": "A caption for the fourth image in the mosaic."
        },
        {
          "URL": "bundle://mosaic-05.jpg",
          "caption": "A caption for the fifth image in the mosaic."
        }
      ]
    },
    {
      "role": "caption",
      "layout": "halfMarginBothLayout",
      "text": "ABOVE: A caption for the entire mosaic. Individual photos in the mosaic also have their own captions. (Shared attribution)"
    },
    {
      "role": "divider",
      "layout": "noMarginLayout",
      "stroke": {
        "width": 1,
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

For example, try changing the order of images in your `mosaic` component by changing URLs:

1.  In your `article.json` file, find the `mosaic` component.

2.  In the first mosaic image’s `URL` property, replace the `01` with `02`.

3.  In the second mosaic image’s `URL` property, replace the `02` with `01`.

4.  Preview your `article.json` file in News Preview.

The order of your first and second images has been switched.

### Previous

Adding a Gallery of Images

### Next

Adding a Tweet

## See Also

### Related Documentation

object Mosaic

The component for displaying a set of images as tiles in no particular order.

object GalleryItem

An object used in a gallery or mosaic component for displaying an individual image.

object Caption

The component for adding caption text.

object CaptionDescriptor

The object you use in image components for displaying captions when the image is full-screen.

### Introductory Design Tutorial

Setting Up the Introductory Tutorial

Download the tutorial files, and learn about what you’ll create in the introductory tutorial.

Creating Your First Article

Create an article with text components and component text styles.

Positioning Text Components

Adjust the positions of the text components in your article—for example, place the article body off-center.

Adding a Divider

Create a horizontal, styled divider that extends to the right edge of the display.

Adding an Image and Captions

Create a photo that extends to both edges of the display, with captions that appear in the article layout and in full-screen view.

Adding a Pull Quote

Break an existing body component into two components, and then insert a pull quote between them.

Adding a Gallery of Images

Display three images as a sequential gallery.

Adding a Tweet

Include a tweet in an article.

Adding a Podcast

Add a link to a podcast that displays the podcast artwork and the podcast show or episode information.

Viewing the Finished Article for the Introductory Design Tutorial

See the full JSON code from this tutorial.

