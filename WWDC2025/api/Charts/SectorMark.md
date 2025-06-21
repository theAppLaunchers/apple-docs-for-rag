*   [Swift Charts](/documentation/charts)
*   SectorMark

Structure

# SectorMark

A sector of a pie or donut chart, which shows how individual categories make up a meaningful total.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor) @preconcurrency
struct SectorMark
```

```
```
```
```
```
```
```

## [Overview](/documentation/Charts/SectorMark#overview)

The relative size of per-category values that make up the total value are mapped to the angular sizes of the sectors.

To ensure that the visualization is easy to read, design pie or donut charts with no more than 5-7 sectors. Sum any remaining values into an “Other” group if necessary, or consider horizontal bar charts, which can scale to many bars, are easy to label with categories, and let users compare items more accurately.

Make sure that your data contains only positive values. Also, very small proportions may not be discernible in the chart, especially if an angular inset is specified.

### [Create a pie chart with sector marks](/documentation/Charts/SectorMark#Create-a-pie-chart-with-sector-marks)

To visualize the ratio of values to the total that they collectively add up to, specify the values, most often ordered by decreasing value. If needed, add an “Other” group as the last item.

```swift
```swift
```swift
```swift
```swift
```swift
let data = [
```
```
    (name: "Cachapa", sales: 9631),
    (name: "Crêpe", sales: 6959),
    (name: "Injera", sales: 4891),
    (name: "Jian Bing", sales: 2506),
    (name: "American", sales: 1777),
    (name: "Dosa", sales: 625),
]
```swift
```swift
var body: some View {
```
```
    Chart(data, id: \.name) { name, sales in
        SectorMark(angle: .value("Value", sales))
            .foregroundStyle(by: .value("Product category", name))
    }
}
```
```
```
```

### [Create and style a donut chart with sector marks](/documentation/Charts/SectorMark#Create-and-style-a-donut-chart-with-sector-marks)

The inner and outer radii can be customized for your design. A non-zero inner radius yields a donut chart. A small angular inset helps accessibility and readability by adding contrast between sectors, which is useful for pie and donut charts. Limit the size of the angular inset and corner radius to small values to avoid distorting the shape and relative size of the sectors.

```swift
```swift
```swift
```swift
```swift
```swift
var body: some View {
```
```
    Chart(data, id: \.name) { name, sales in
        SectorMark(
            angle: .value("Value", sales),
            innerRadius: .ratio(0.618),
            outerRadius: .inset(10),
            angularInset: 1
        )
        .cornerRadius(4)
        .foregroundStyle(by: .value("Product category", name))
    }
}
```
```
```
```

## [Topics](/documentation/Charts/SectorMark#topics)

### [Initializers](/documentation/Charts/SectorMark#Initializers)

[`init(angle: PlottableValue<some Plottable>, innerRadius: MarkDimension, outerRadius: MarkDimension, angularInset: CGFloat?)`](/documentation/charts/sectormark/init\(angle:innerradius:outerradius:angularinset:\))

Creates a sector mark, which uses the angular size to represent the proportion of the value to the sum of all values.

## [Relationships](/documentation/Charts/SectorMark#relationships)

### [Conforms To](/documentation/Charts/SectorMark#conforms-to)

*   [`ChartContent`](/documentation/charts/chartcontent)
*   [`Copyable`](/documentation/Swift/Copyable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/Charts/SectorMark#see-also)

### [Marks](/documentation/Charts/SectorMark#Marks)

```swift
```swift
```swift
```swift
struct AreaMark
```
```

Chart content that represents data using the area of one or more regions.
```
```swift
```swift
```swift
struct LineMark
```
```

Chart content that represents data using a sequence of connected line segments.
```
```swift
```swift
```swift
struct PointMark
```
```

Chart content that represents data using points.
```
```swift
```swift
```swift
struct RectangleMark
```
```

Chart content that represents data using rectangles.
```
```swift
```swift
```swift
struct RuleMark
```
```

Chart content that represents data using a single horizontal or vertical rule.
```
```swift
```swift
```swift
struct BarMark
```
```

Chart content that represents data using bars.
```
```