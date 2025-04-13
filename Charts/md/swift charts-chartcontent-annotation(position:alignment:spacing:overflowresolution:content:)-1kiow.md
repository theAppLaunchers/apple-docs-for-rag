

- Swift Charts
- ChartContent
-  annotation(position:alignment:spacing:overflowResolution:content:) 

Instance Method

# annotation(position:alignment:spacing:overflowResolution:content:)

Annotates this mark or collection of marks with a view positioned relative to its bounds.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
nonisolated
func annotation(
    position: AnnotationPosition = .automatic,
    alignment: Alignment = .center,
    spacing: CGFloat? = nil,
    overflowResolution: AnnotationOverflowResolution,
    @ViewBuilder content: () -> C
) -> some ChartContent where C : View
```

## Parameters 

`position`  

The location relative to the item being annotated at which the annotation will be placed.

`alignment`  

The guide for aligning the annotation in the specified position.

`spacing`  

Distance between the annotation and the annotated content, or `nil` if you want to use the default distance.

`overflowResolution`  

How to resolve the annotation exceeding the boundary of the plot.

`content`  

A view builder that creates the annotation. The builder takes one input which provides information regarding the item being annotated such as its size.

