

- RealityKit
- RealityViewAttachmentBuilderContent
-  gridCellUnsizedAxes(\_:) 

Instance Method

# gridCellUnsizedAxes(\_:)

Asks grid layouts not to offer the view extra size in the specified axes.

RealityKitSwiftUIiOS 16.0+iPadOS 16.0+macOS 13.0+tvOS 16.0+visionOSwatchOS 9.0+

``` source
nonisolated
func gridCellUnsizedAxes(_ axes: Axis.Set) -> some View
```

## Parameters 

`axes`  

The dimensions in which the grid shouldn’t offer the view a share of any available space. This prevents a flexible view like a `Spacer`, `Divider`, or `Color` from defining the size of a row or column.

## Return Value

A view that doesn’t ask an enclosing grid for extra size in one or more axes.

## Discussion

Use this modifier to prevent a flexible view from taking more space on the specified axes than the other cells in a row or column require. For example, consider the following `Grid` that places a `Divider` between two rows of content:

```
Grid {
    GridRow {
        Text("Hello")
        Image(systemName: "globe")
    }
    Divider()
    GridRow {
        Image(systemName: "hand.wave")
        Text("World")
    }
}
```

The text and images all have ideal widths for their content. However, because a divider takes as much space as its parent offers, the grid fills the width of the display, expanding all the other cells to match:

You can prevent the grid from giving the divider more width than the other cells require by adding the modifier with the `Axis/horizontal` parameter:

```
Divider()
    .gridCellUnsizedAxes(.horizontal)
```

This restores the grid to the width that it would have without the divider:

