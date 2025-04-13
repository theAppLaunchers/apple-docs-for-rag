

- Swift Charts
- AxisValueLabel
-  init(centered:anchor:multiLabelAlignment:collisionResolution:offsetsMarks:orientation:horizontalSpacing:verticalSpacing:) 

Initializer

# init(centered:anchor:multiLabelAlignment:collisionResolution:offsetsMarks:orientation:horizontalSpacing:verticalSpacing:)

Constructs axis value labels with the given properties and default text.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
nonisolated
init(
    centered: Bool? = nil,
    anchor: UnitPoint? = nil,
    multiLabelAlignment: Alignment? = nil,
    collisionResolution: AxisValueLabelCollisionResolution = .automatic,
    offsetsMarks: Bool? = nil,
    orientation: AxisValueLabelOrientation = .automatic,
    horizontalSpacing: CGFloat? = nil,
    verticalSpacing: CGFloat? = nil
) where Content == Never
```

## Parameters 

`centered`  

Whether to center the label between two axis values. If `nil`, default to true for discrete data, false to continuous data.

`anchor`  

The anchor point on the bounding box of the text element that attaches to the `position`.

`multiLabelAlignment`  

How labels along the axis are aligned with each other.

`collisionResolution`  

How labels that collide with others are resolved.

`offsetsMarks`  

Whether to offset marks to accomodate for the space used by the label.

`orientation`  

The orientation of the label.

`horizontalSpacing`  

The horizontal spacing of the label. If `nil`, a default spacing will be used.

`verticalSpacing`  

The vertical spacing of the label. If `nil`, a default spacing will be used.

