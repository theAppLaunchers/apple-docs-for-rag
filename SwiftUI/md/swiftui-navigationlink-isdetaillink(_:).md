

- SwiftUI
- NavigationLink
-  isDetailLink(\_:) 

Instance Method

# isDetailLink(\_:)

Sets the navigation link to present its destination as the detail component of the containing navigation view.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+visionOS 1.0+

``` source
func isDetailLink(_ isDetailLink: Bool) -> some View
```

Available when `Label` conforms to `View` and `Destination` conforms to `View`.

## Parameters 

`isDetailLink`  

A Boolean value that specifies whether this link presents its destination as the detail component when used in a multi-column navigation view.

## Return Value

A view that applies the specified detail link behavior.

## Discussion

This method sets the behavior when the navigation link is used in a NavigationSplitView, or a multi-column navigation view, such as one using ColumnNavigationViewStyle.

For example, in a two-column navigation split view, if `isDetailLink` is `true`, triggering the link in the sidebar column sets the contents of the detail column to be the link’s destination view. If `isDetailLink` is `false`, the link navigates to the destination view within the primary column.

If you do not set the detail link behavior with this method, the behavior defaults to `true`.

The `isDetailLink` modifier only affects view-destination links. Links that present data values always search for a matching navigation destination beginning in the column that contains the link.

