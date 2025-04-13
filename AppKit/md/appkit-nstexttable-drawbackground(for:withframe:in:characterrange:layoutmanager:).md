

- AppKit
- NSTextTable
-  drawBackground(for:withFrame:in:characterRange:layoutManager:) 

Instance Method

# drawBackground(for:withFrame:in:characterRange:layoutManager:)

Draws any colors and other decorations for a text table block.

macOS

``` source
func drawBackground(
    for block: NSTextTableBlock,
    withFrame frameRect: NSRect,
    in controlView: NSView,
    characterRange charRange: NSRange,
    layoutManager: NSLayoutManager
)
```

## Parameters 

`block`  

The text table block that wants to draw its background.

`frameRect`  

The area in which drawing occurs.

`controlView`  

The view controlling the drawing.

`charRange`  

The range of the characters whose glyphs are to be drawn.

`layoutManager`  

The layout manager controlling the typesetting.

## Discussion

This methods is called by the text table block `block` to draw any colors and other decorations before the text is drawn.

