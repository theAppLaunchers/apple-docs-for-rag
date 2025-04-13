

- Apple News
- Apple News Format Tutorials
-  Creating Your First Article 

Article

# Creating Your First Article

Create an article with text components and component text styles.

## Overview

In Setting Up the Introductory Tutorial, you learned how to download the article structure bundle. To create an article, you must add some JSON objects (called *components*) to that bundle.

**On this page, you’ll learn how to add:**

- Simple text components representing article content

- Component text style defaults

- A drop cap

### Add Text Components to the Article Structure

Components represent the content of your article, including the article’s title, introduction, byline, and body text.

The example code Components: Copy This Code is long, but you don’t need to understand all of it yet. All you’ll do here is copy and paste it.

1.  Open the `article.json` file in the `News_Design_Tutorial_1_Article_Structure` folder that you created in Download the Article Bundle Examples.

2.  Copy the example code Components: Copy This Code.

3.  In your working `article.json` `file`, select this line: `"components": [],`

4.  Paste the copied code into `article.json`, replacing the line that you selected in the previous step.

You have added fifteen components to your article.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see your content on the simulated device, without any added styles or layout.

The body content in the example is in HTML. For details about using HTML tags to format articles, see Using HTML with Apple News Format.

Important

Make sure to save your `article.json` file. Do not change the file name.

#### Components: Copy This Code

```
  "components": [
    {
      "role": "heading1",
      "text": "HEADING"
    },
    {
      "role": "title",
      "text": "ARTICLE TITLE"
    },
    {
      "role": "intro",
      "text": "Etiam rhoncus. Maecenas tempus, tellus eget condimentum rhoncus, sem quam semper libero, sit amet adipiscing sem neque ipsum?"
    },
    {
      "role": "byline",
      "text": "By Urna Semper"
    },
    {
      "role": "body",
      "format": "html",
      "text": "Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat facere possimus, omnis voluptas assumenda est, dolor repellendus. Link text quibusdam et aut.Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, adipisci velit."
    },
    {
      "role": "heading2",
      "text": "HEADING"
    },
    {
      "role": "body",
      "format": "html",
      "text": "Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla pariatur? At vero eos et accusamus et iusto odio ducimus qui blanditiis.Cras ultricies mi eu turpis hendrerit fringilla. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; In ac dui quis mi consectetuer.Temporibus autem et aut officiis debitis aut rerum necessitatibus saepe eveniet ut et voluptates repudiandae sint et molestiae non recusandae. Itaque rerum hic tenetur.Inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo esciunt enim ipsam voluptatem quia.Ut aut reiciendis voluptatibus maiores alias consequatur aut perferendis link text repellat. Sed ut perspiciatis unde omnis iste natus sit voluptatem accusantium doloremque, totam rem aperiam, eaque ipsa quae ab illo inventore.Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni."
    },
    {
      "role": "heading2",
      "text": "HEADING"
    },
    {
      "role": "body",
      "format": "html",
      "text": "Sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas."
    },
    {
      "role": "heading2",
      "text": "HEADING"
    },
    {
      "role": "body",
      "format": "html",
      "text": "Et harum quidem rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat facere possimus, omnis voluptas est, omnis dolor repellendus."
    },
    {
      "role": "heading2",
      "text": "HEADING"
    },
    {
      "role": "body",
      "format": "html",
      "text": "Consequatur aut doloribus asperiores repellat. Sed ut perspiciatis unde omnis iste natus error sit volup tatem accusantium doloremque laudantium, totam rem, eaque ipsa quae ab illo inventore veritatis et quasi archit ecto beatae vitae.Nemo enim ipsam volup tatem quia voluptas sit aspernatur aut odit aut fugit, sed quia conse quuntur magni. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam.Consequatur aut perferendis doloribus asperiores repellat. Sed ut perspiciatis unde omnis iste natus error sit volup tatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi archit ecto beatae vitae dicta. Nemo enim ipsam volup tatem quia voluptas sit link text aut odit aut fugit, sed quia conse quuntur perspiciatis doloribus magni dolores.Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam suscipit laboriosam."
    },
    {
      "role": "heading2",
      "text": "HEADING"
    },
    {
      "role": "body",
      "format": "html",
      "text": "Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla pariatur? At vero eos et accusamus et iusto odio. Dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati."
    }
  ],
```

### Apply a Default Text Style to the Article

You should always include a default text style to ensure a consistent appearance for the text components in your article. You can always override the default style, as needed, for one or more components.

1.  Copy the example code Default Text Style: Copy This Code.

2.  Paste the code inside the `ArticleDocument.componentTextStyles` object in your `article.json` file, after the opening brace (`{`).

Your code should look like the example code Default Text Style: Result.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see that all of your components are now using the `default` text style. You can tell because the text in the preview is bold and link text is yellow.

#### Default Text Style: Copy This Code

```
    "default": {
      "fontName": "DINAlternate-Bold",
      "textColor": "#222222",
      "fontSize": 16,
      "lineHeight": 22,
      "linkStyle": {
        "textColor": "#D5B327"
      }
    }
```

#### Default Text Style: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "componentTextStyles": {
    "default": {
      "fontName": "DINAlternate-Bold",
      "textColor": "#222222",
      "fontSize": 16,
      "lineHeight": 22,
      "linkStyle": {
        "textColor": "#D5B327"
      }
    }
  }
}
```

### Apply Default Text Styles by Component Role

Default `role`-specific component text styles ensure a consistent text style across all components with a given `role`, such as all `heading` components or all `body` components. You can always override these default styles, as needed, for one or more components.

1.  Copy the example code Default Component Text Styles: Copy This Code.

2.  Paste the code inside the `ArticleDocument.componentTextStyles` object in your `article.json` file, after the closing brace (`}`) for the content that you added in Apply a Default Text Style to the Article.

Your code should look like the example code Default Component Text Styles: Result.

This code adds default text styles for `body`, `title`, and other component types. The properties in these `role`-specific text styles override the same properties in the article’s default text style.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see that your article’s components now use the default component text styles for their types. For example, article body text uses a serif font, and the first four components in your article have gray text instead of black.

#### Default Component Text Styles: Copy This Code

```
,
    "default-body": {
      "fontName": "IowanOldStyle-Roman",
      "paragraphSpacingBefore": 12,
      "paragraphSpacingAfter": 12
    },
    "default-title": {
      "fontName": "DINAlternate-Bold",
      "fontSize": 42,
      "lineHeight": 44,
      "textColor": "#53585F"
    },
    "default-intro": {
      "fontName": "DINAlternate-Bold",
      "fontSize": 18,
      "lineHeight": 22,
      "textColor": "#A6AAA9"
    },
    "default-byline": {
      "fontName": "DINAlternate-Bold",
      "fontSize": 15,
      "lineHeight": 18,
      "textColor": "#53585F"
    },
    "default-heading2": {
      "fontName": "DINAlternate-Bold",
      "tracking": 0.05,
      "textColor": "#53585F"
    },
    "default-heading1": {
      "fontName": "DINAlternate-Bold",
      "tracking": 0.12,
      "textColor": "#53585F"
    }
```

#### Default Component Text Styles: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "componentTextStyles": {
    "default-body": {
      "fontName": "IowanOldStyle-Roman",
      "paragraphSpacingBefore": 12,
      "paragraphSpacingAfter": 12
    },
    "default-title": {
      "fontName": "DINAlternate-Bold",
      "fontSize": 42,
      "lineHeight": 44,
      "textColor": "#53585F"
    },
    "default-intro": {
      "fontName": "DINAlternate-Bold",
      "fontSize": 18,
      "lineHeight": 22,
      "textColor": "#A6AAA9"
    },
    "default-byline": {
      "fontName": "DINAlternate-Bold",
      "fontSize": 15,
      "lineHeight": 18,
      "textColor": "#53585F"
    },
    "default-heading2": {
      "fontName": "DINAlternate-Bold",
      "tracking": 0.05,
      "textColor": "#53585F"
    },
    "default-heading1": {
      "fontName": "DINAlternate-Bold",
      "tracking": 0.12,
      "textColor": "#53585F"
    }
  }
}
```

### Define a Style That Has a Drop Cap

A drop cap changes the size, position, and style of a text component’s first character, or first few characters. Before you can add a drop cap to a text component, you must define a style that has a drop cap.

Note

The drop cap text style was named `dropCapStyle` for this tutorial, but when you create your own articles, you can create your own component and style names.

1.  Copy the example code bodyFirstDropCap: Copy This Code.

2.  Paste the code inside the `ArticleDocument.componentTextStyles` object in your `article.json` file, after the closing brace (`}`) of the last `ComponentTextStyle` object and before the closing brace for the whole `componentTextStyles` property.

Your code should look like the example code bodyFirstDropCap: Result.

#### bodyFirstDropCap: Copy This Code

```
,
    "bodyFirstDropCap": {
      "dropCapStyle": {
        "fontName": "DINAlternate-Bold",
        "textColor": "#A6AAA9",
        "numberOfLines": 2
      }
    }
```

#### bodyFirstDropCap: Result

Ellipses (`...`) indicate lines of code that have been omitted from this example.

```
{
  ...
  "componentTextStyles": {
    ...
    "bodyFirstDropCap": {
      "dropCapStyle": {
        "fontName": "DINAlternate-Bold",
        "textColor": "#A6AAA9",
        "numberOfLines": 2
      }
    }
  }
}
```

### Use the Drop Cap Style in a Body Component

Now that you have defined a style with a drop cap, you can use that style in one or more components.

Add this line inside your article’s first body component:

`"textStyle": "bodyFirstDropCap",`

Your code should look like the example code Drop Cap Style: Result.

After you make this change in your code, you can preview your working `article.json` file in News Preview to see a drop cap in your article.

#### Drop Cap Style: Result

Ellipses (…) indicate lines of code that have been omitted from this example.

```
{
  ...
  "components": [
    ...
    {
      "role": "body",
      "format": "html",
      "textStyle": "bodyFirstDropCap",
      "text": "Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat facere possimus, omnis voluptas assumenda est, dolor repellendus. Link text quibusdam et aut.Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, adipisci velit."
    },
    ...
  ],
  ...
}
```

### Further Exploration

At any time, you can try changing property values in your `article.json` file and then use News Preview to see how these changes affect the look of your article.

For example, try changing the height of your article’s drop cap:

1.  In your `article.json` file, find the `ComponentTextStyle` object called `bodyFirstDropCap`.

2.  In `bodyFirstDropCap`, find the `numberOfLines` property.

3.  Replace the value of the `numberOfLines` property, `2`, with a number of your choice between 2 and 10.

4.  Preview your `article.json` file in News Preview.

The drop cap in your article now uses the new height that you chose. If you chose a number less than 2 or greater than 10, the error console informs you that you chose an illegal value. On some devices, the height of the drop cap may be adjusted automatically to help ensure a better visual experience.

### Next

Positioning Text Components

## See Also

### Related Documentation

Defining and Applying Text Styles

Define and apply custom, default, and inline text styles, or use HTML tags or Markdown syntax to style your text.

Using HTML with Apple News Format

Use HTML formatting for text components.

Applying Apple News Format Fonts

Choose a font family for Apple News Format that’s supported in iOS, iPadOS, and macOS.

Components

Understand the types of components that can make up an article.

object ComponentTextStyle

The object for defining the style for a text component, including spacing, alignment, and drop caps.

object DropCapStyle

The object for defining the drop cap text style to use in the first paragraph in a text component.

### Introductory Design Tutorial

Setting Up the Introductory Tutorial

Download the tutorial files, and learn about what you’ll create in the introductory tutorial.

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

Adding a Mosaic of Images

Display five images as mosaic tiles.

Adding a Tweet

Include a tweet in an article.

Adding a Podcast

Add a link to a podcast that displays the podcast artwork and the podcast show or episode information.

Viewing the Finished Article for the Introductory Design Tutorial

See the full JSON code from this tutorial.

