

- App Intents
- SiriTipView
-  listItemTint(\_:) 

Instance Method

# listItemTint(\_:)

Sets a fixed tint color for content in a list.

AppIntentsSwiftUIiOS 14.0+iPadOS 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
nonisolated
func listItemTint(_ tint: Color?) -> some View
```

## Parameters 

`tint`  

The color to use to tint the content. Use `nil` to avoid overriding the inherited tint.

## Discussion

The containing list’s style applies the tint as appropriate. For example, watchOS uses the tint color for its background platter appearance. Sidebars on iOS and macOS apply the tint color to their `Label` icons, which otherwise use the accent color by default.

Note

This modifier is equivalent to using the version of the modifier that takes a `ListItemTint` value and specifying the `tint` color in the corresponding `ListItemTint/fixed(_:)` input.

