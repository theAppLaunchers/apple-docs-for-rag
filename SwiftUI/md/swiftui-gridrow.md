

- SwiftUI
-  GridRow 

Structure

# GridRow

A horizontal row in a two dimensional grid container.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
@frozen
struct GridRow where Content : View
```

## Overview

Use one or more `GridRow` instances to define the rows of a Grid container. The child views inside the row define successive grid cells. You can add rows to the grid explicitly, or use the ForEach structure to generate multiple rows. Similarly, you can add cells to the row explicitly or you can use ForEach to generate multiple cells inside the row. The following example mixes these strategies:

```
Grid {
    GridRow {
        Color.clear
            .gridCellUnsizedAxes([.horizontal, .vertical])
        ForEach(1..

The grid in the example above has an explicit first row and three generated rows. Similarly, each row has an explicit first cell and three generated cells:

To create an empty cell, use something invisible, like the clear color that appears in the first column of the first row in the example above. However, if you use a flexible view like a Color or a Spacer, you might also need to add the gridCellUnsizedAxes(_:) modifier to prevent the view from taking up more space than the other cells in the row or column need.

Important

You can’t use EmptyView to create a blank cell because that resolves to the absence of a view and doesn’t generate a cell.

By default, the cells in the row use the Alignment that you define when you initialize the Grid. However, you can override the vertical alignment for the cells in a row by providing a VerticalAlignment value to the row’s init(alignment:content:) initializer.

If you apply a view modifier to a row, the row applies the modifier to all of the cells, similar to how a Group behaves. For example, if you apply the border(_:width:) modifier to a row, SwiftUI draws a border on each cell in the row rather than around the row.

## Topics

### Creating a grid row

init(alignment: VerticalAlignment?, content: () -> Content)

Creates a horizontal row of child views in a grid.

## Relationships

### Conforms To

- Copyable
- View

  Conforms when `Content` conforms to `View`.

## See Also

### Statically arranging views in two dimensions

struct Grid

A container view that arranges other views in a two dimensional layout.

func gridCellColumns(Int) -> some View

Tells a view that acts as a cell in a grid to span the specified number of columns.

func gridCellAnchor(UnitPoint) -> some View

Specifies a custom alignment anchor for a view that acts as a grid cell.

func gridCellUnsizedAxes(Axis.Set) -> some View

Asks grid layouts not to offer the view extra size in the specified axes.

func gridColumnAlignment(HorizontalAlignment) -> some View

Overrides the default horizontal alignment of the grid column that the view appears in.

