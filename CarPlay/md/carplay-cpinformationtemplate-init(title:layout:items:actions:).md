

- CarPlay
- CPInformationTemplate
-  init(title:layout:items:actions:) 

Initializer

# init(title:layout:items:actions:)

Creates an information template that displays the provided items using the chosen layout.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

``` source
init(
    title: String,
    layout: CPInformationTemplateLayout,
    items: [CPInformationItem],
    actions: [CPTextButton]
)
```

## Parameters 

`title`  

The title that the template displays.

`layout`  

The layout that the template uses to arrange its items. See CPInformationTemplateLayout for more information.

`items`  

An array of information items that the template displays.

`actions`  

An array of text buttons that provides the actions that the user can perform.

## Discussion

The template can display up to 10 information items. If `items` contains more objects, the template uses only the first 10. Likewise, the template displays three actions maximum. If `actions` contains more than that, the template uses only the first three.

