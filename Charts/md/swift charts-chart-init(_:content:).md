

- Swift Charts
- Chart
-  init(\_:content:) 

Initializer

# init(\_:content:)

Creates a chart composed of a series of identifiable marks.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
nonisolated
init(
    _ data: Data,
    @ChartContentBuilder content: @escaping (Data.Element) -> C
) where Content == ForEach, Data : RandomAccessCollection, C : ChartContent, Data.Element : Identifiable
```

## Parameters 

`data`  

A collection of data that conforms to the Identifiable protocol.

`content`  

The mark that the chart should draw for each element in the data collection.

## Discussion

This initializer wraps the data that you provide as input in an implicit ForEach structure. If you need to represent more than one series in your chart, use init(content:) instead.

## See Also

### Creating a chart

init(content: () -> Content)

Creates a chart composed of any number of data series and individual marks.

init&lt;Data, ID, C>(Data, id: KeyPath&lt;Data.Element, ID>, content: (Data.Element) -> C)

Creates a chart composed of a series of marks.

