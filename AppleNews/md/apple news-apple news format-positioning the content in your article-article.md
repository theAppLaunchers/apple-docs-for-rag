

- Apple News
- Apple News Format
-  Positioning the Content in Your Article 

Article

# Positioning the Content in Your Article

Align article components with columns in your layout.

## Overview

You set the number of columns you want in your design using the `layout` property of Article Document. To determine the position for a component, like a heading, you align the left edge of the component with a column in your layout. (The component automatically lines up with the left edge of the column.) See Layout and Planning the Layout for Your Article.

Layout columns are numbered from left to right starting with 0. You use this column system to figure out the positioning for all the components in your article and then, in your `article.json` file, you use a ComponentLayout object to specify the position settings.

### Specify Positions for Components

Specify the starting column and how many columns you want a component to span. For example, in the previous figure, a pull quote component is positioned at column 0 and spans three columns. The figure also shows a caption component positioned at column 7 that spans three columns.

To specify the positioning for components, you create a component layout object at one of two levels. If you create a component layout object in ArticleDocument.componentLayouts, multiple components can refer to it. Two components that use the same component layout object start in the same column, span the same number of columns, and so on.

If you create a component layout object as a property for a specific component, only that component can use it.

The following code example shows a component layout object called `heading1Layout`. This component layout object has been created in ArticleDocument.componentLayouts so other components in the article can use it.

```
"componentLayouts": {
   "heading1Layout": {
      "columnStart": 0,
      "columnSpan": 6,
      "margin": {
        "top": 24,
        "bottom": 3
      }
   }
}
```

Tip

For best results, the sum of the `columnStart` value and the `columnSpan` value shouldn’t exceed the number of columns available for the component. Otherwise, your article may not render as expected.

### Fine-Tune the Position of Components

You can use the `margin` property of a ComponentLayout object to specify the top and bottom margins (in points) for a component and to create space above and below the component. Specify a single number to use for both measurements, or — to specify different settings for the top and bottom margins — use the Margin object.

In addition to using `margin`, you can also use the `padding` property of the `ComponentLayout` object to define the space inside a component. With the `padding` property, you can set spacing for both sides of the component, as well as for the top and bottom. The `padding` property is different from margins in that it applies to the spacing *inside* the component; margins are applied to the spacing of the component within the article.

An Anchor object located within the component object lets you associate the placement of one component with another component so you can align components vertically in your layout. The position of the target component determines the position of the component that has the anchor.

Horizontally align the contents of a component within the component. (This property applies only to Image, Logo, and Divider components.)

Tip

To position text *within* a component, such as for centered text or for a drop cap, use the ComponentTextStyle object for the individual component.

### Align and Position Content

To make your content span the entire device screen, use the `ignoreViewportPadding` property of the ComponentLayout object.

In the following code example, `ignoreViewportPadding` is set to `true` for the `image` object, which causes Apple News to ignore padding on both sides of the screen.

```
{
  "components": [
    {
      "role": "title",
      "text": "Article Title"
    },
    {
      "role": "image",
      "URL": "bundle://summer.jpg",
      "caption": "Thanks to the record drought, mountain lions have begun to descend from the peaks.",
      "layout": {
        "ignoreViewportPadding": true
      }
    }
  ]
}
```

To make content extend past the columns of your article layout and into the margin that you added, but not into the extra padding the Apple News app adds, use the `ignoreDocumentMargin` property of the ComponentLayout object. This property allows a component to be full width on most screens, while preventing it from growing too wide on very wide screens like a Mac computer. Use `ignoreDocumentMargin` only if you haven’t specified a value for `ignoreViewportPadding`.

In the following code example, the `image` object ignores the left and right margins specified in the document layout and spans the full width and the margin of the document. See Layout.

```
{
  "components": [
    {
      "role": "title",
      "text": "Article Title"
    },
    {
      "role": "image",
      "URL": "bundle://summer.jpg",
      "caption": "Thanks to the record drought, mountain lions have begun to descend from the peaks.",
      "layout": {
        "ignoreDocumentMargin": true
      }
    }
  ]
}
```

#### What Changed in iOS 13, iPadOS 13, and macOS 10.15

Prior to iOS 13, iPadOS 13, and macOS 10.15, the `ignoreDocumentMargin` property of the ComponentLayout object caused a component to span the entire screen.

Starting in iOS 13, iPadOS 13, and macOS 10.15, the `ignoreDocumentMargin` property of the `ComponentLayout` object now allows a component to span the entire screen until the screen becomes wider than the document `margin` and the document `width` combined.

To make a component span the entire screen, regardless of the screen width, use the `ignoreViewportPadding` property of the `ComponentLayout` object.

If you previously used the `ignoreDocumentMargin` property, you must update your `article.json` file to use the `ignoreViewportPadding` property instead.

The following figure shows an `image` object with `ignoreViewportPadding` set to `true`.

To make the image object span only the document width plus margin, set `ignoreDocumentMargin` to `true` and `ignoreViewportPadding` to `false`.

## See Also

### Article Layout

Planning the Layout for Your Article

Define a layout that supports the look you want for your article.

Wrapping Text Around a Component

Define the layout of a text component to wrap around another component.

object Layout

The object for defining columns, gutters, and margins for your article’s designed width.

object ComponentLayout

The object for defining the positioning for a specific component within the article’s column system.

object Anchor

The object for anchoring one component to another component in your article’s layout.

object Margin

The object for defining the space above and below a component.

object AutoPlacementLayout

The object for defining the margin above and below advertising components.

object AdvertisingLayout

The object for defining the margin above and below advertising components.

Deprecated

