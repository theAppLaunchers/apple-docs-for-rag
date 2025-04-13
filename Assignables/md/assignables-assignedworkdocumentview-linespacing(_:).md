

- Assignables
- AssignedWorkDocumentView
-  lineSpacing(\_:) 

Instance Method

# lineSpacing(\_:)

Sets the amount of space between lines of text in this view.

AssignablesSwiftUIiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOSwatchOS 6.0+

``` source
nonisolated
func lineSpacing(_ lineSpacing: CGFloat) -> some View
```

## Parameters 

`lineSpacing`  

The amount of space between the bottom of one line and the top of the next line in points.

## Discussion

Use `lineSpacing(_:)` to set the amount of spacing from the bottom of one line to the top of the next for text elements in the view.

In the `Text` view in the example below, 10 points separate the bottom of one line to the top of the next as the text field wraps inside this view. Applying `lineSpacing(_:)` to a view hierarchy applies the line spacing to all text elements contained in the view.

```
Text("This is a string in a TextField with 10 point spacing applied between the bottom of one line and the top of the next.")
    .frame(width: 200, height: 200, alignment: .leading)
    .lineSpacing(10)
```

