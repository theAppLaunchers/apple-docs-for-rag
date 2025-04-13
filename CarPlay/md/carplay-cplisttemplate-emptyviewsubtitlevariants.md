

- CarPlay
- CPListTemplate
-  emptyViewSubtitleVariants 

Instance Property

# emptyViewSubtitleVariants

An array of subtitle variants for the template’s empty view.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

``` source
var emptyViewSubtitleVariants: [String] { get set }
```

## Discussion

When the list contains zero items, the template displays an empty view with a title and a subtitle. The template removes the empty view if you update the list and provide items.

Provide at least one nonzero length subtitle variant. The view displays the first subtitle variant that fits into the available screen space, so arrange your variants array from most- to least-preferred. Provide the strings as localized displayable content.

## See Also

### Managing an Empty List

var emptyViewTitleVariants: [String]

An array of title variants for the template’s empty view.

