Framework

# Swift Charts

Construct and customize charts on every Apple platform.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

## [Overview](/documentation/Charts#Overview)

Swift Charts is a powerful and concise SwiftUI framework you can use to transform your data into informative visualizations. With Swift Charts, you can build effective and customizable charts with minimal code. This framework provides marks, scales, axes, and legends as building blocks that you can combine to develop a broad range of data-driven charts.

![A graphic showing three charts built with Swift Charts: a line chart, a bar chart, and a scatter plot.](https://docs-assets.developer.apple.com/published/39f0be0768748aef1d94764a618561a0/FrameworkOverview%402x.png)

There are many ways you can use Swift Charts to communicate patterns or trends in your data. You can create a variety of charts including line charts, bar charts, and scatter plots as shown above. When you create a chart using this framework, it automatically generates scales and axes that fit your data.

Swift Charts supports localization and accessibility features. You can also override default behavior to customize your charts by using chart modifiers. For example, you can create a dynamic experience by adding animations to your charts.

## [Topics](/documentation/Charts#topics)

### [Essentials](/documentation/Charts#Essentials)

[

Swift Charts updates](/documentation/Updates/SwiftCharts)

Learn about important changes to Swift Charts.

### [Charts](/documentation/Charts#Charts)

[

Creating a chart using Swift Charts](/documentation/charts/creating-a-chart-using-swift-charts)

Make a chart by combining chart building blocks in SwiftUI.

[

Visualizing your app’s data](/documentation/charts/visualizing_your_app_s_data)

Build complex and interactive charts using Swift Charts.

```swift
```swift
```swift
struct Chart
```
```

A SwiftUI view that displays a chart.
```
```swift
```swift
```swift
protocol ChartContent
```
```

A type that represents the content that you draw on a chart.
```
```swift
```swift
```swift
struct ChartContentBuilder
```
```

A result builder that you use to compose the contents of a chart.
```
```swift
```swift
```swift
struct Plot
```
```

A mechanism for grouping chart contents into a single entity.
```

### [Marks](/documentation/Charts#Marks)

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
```swift
```swift
```swift
struct SectorMark
```
```

A sector of a pie or donut chart, which shows how individual categories make up a meaningful total.
```
```

### [Vectorized plots](/documentation/Charts#Vectorized-plots)

[

Creating a data visualization dashboard with Swift Charts](/documentation/charts/creating-a-data-visualization-dashboard-with-swift-charts)

Visualize an entire data collection efficiently by instantiating a single vectorized plot in Swift Charts.

```swift
```swift
```swift
struct AreaPlot
```
```

Chart content that represents a function or a collection of data using the area of one or more regions.
```
```swift
```swift
```swift
struct LinePlot
```
```

Chart content that represents a function or a collection of data using a sequence of connected line segments.
```
```swift
```swift
```swift
struct PointPlot
```
```

Chart content that represents a collection of data using points.
```
```swift
```swift
```swift
struct RectanglePlot
```
```

Chart content that represents a collection of data using rectangles.
```
```swift
```swift
```swift
struct RulePlot
```
```

Chart content that represents a collection of data using a single horizontal or vertical rule.
```
```swift
```swift
```swift
struct BarPlot
```
```

Chart content that represents a collection of data using bars.
```
```swift
```swift
```swift
struct SectorPlot
```
```

Chart content that represents a collection of data using a sector of a pie or donut chart, which shows how individual categories make up a meaningful total.
```
```swift
```swift
```swift
protocol VectorizedChartContent
```
```

A generic type that represents content conveyed via a chart.
```

### [Mark configuration](/documentation/Charts#Mark-configuration)

```swift
```swift
```swift
```swift
struct MarkStackingMethod
```
```

The ways in which you can stack marks in a chart.
```
```swift
```swift
```swift
struct MarkDimension
```
```

An individual dimension representing a mark’s width or height.
```
```swift
```swift
```swift
struct InterpolationMethod
```
```

The ways in which line or area marks interpolate their data.
```
```swift
```swift
```swift
struct BasicChartSymbolShape
```
```

A basic chart symbol shape.
```
```swift
```swift
```swift
protocol ChartSymbolShape
```
```

A type that can act as a shape for the marks that you add to a chart.
```
```swift
```swift
```swift
struct AnyChartSymbolShape
```
```

A type-erased plotting shape.
```
```

### [Labeled data](/documentation/Charts#Labeled-data)

```swift
```swift
```swift
```swift
struct PlottableValue
```
```

Labeled data that you plot in a chart using marks.
```
```swift
```swift
```swift
protocol Plottable
```
```

A type that can serve as data to plot in a chart.
```
```

### [Scales](/documentation/Charts#Scales)

```swift
```swift
```swift
```swift
protocol ScaleRange
```
```

A type that you can use to configure the range of a chart.
```
```swift
```swift
```swift
protocol PositionScaleRange
```
```

A type that configures the x-axis and y-axis values.
```
```swift
```swift
```swift
struct PlotDimensionScaleRange
```
```

A range that represents the plot area’s width or height.
```
```swift
```swift
```swift
protocol ScaleDomain
```
```

A type that you can use to configure the domain of a chart.
```
```swift
```swift
```swift
struct AutomaticScaleDomain
```
```

A domain that the chart infers from its data.
```
```swift
```swift
```swift
struct ScaleType
```
```

The ways you can scale the domain or range of a plot.
```
```

### [Axes](/documentation/Charts#Axes)

[

Customizing axes in Swift Charts](/documentation/charts/customizing-axes-in-swift-charts)

Improve the clarity of your chart by configuring the appearance of its axes.

```swift
```swift
```swift
struct ChartAxisContent
```
```

A view that represents a chart’s axis.
```
```swift
```swift
```swift
protocol AxisContent
```
```

A type that represents the elements you use to build a chart’s axes.
```
```swift
```swift
```swift
struct AxisMarks
```
```

A group of visual marks that a chart draws to indicate the composition of a chart’s axes.
```
```swift
```swift
```swift
struct AnyAxisContent
```
```

A type-erased element of a chart’s axis.
```
```swift
```swift
```swift
struct AxisContentBuilder
```
```

A result builder that constructs axis content.
```

### [Axis marks](/documentation/Charts#Axis-marks)

```swift
```swift
```swift
```swift
protocol AxisMark
```
```

A type that serves as the basic building block for the elements of an axis.
```
```swift
```swift
```swift
struct AxisTick
```
```

A mark that a chart draws on an axis to indicate a reference point along that axis.
```
```swift
```swift
```swift
struct AxisGridLine
```
```

A line that a chart draws across its plot area to indicate a reference point along a particular axis.
```
```swift
```swift
```swift
struct AxisValueLabel
```
```

A label that describes the value for an axis mark.
```
```swift
```swift
```swift
struct AxisValue
```
```

A value for an axis mark.
```
```swift
```swift
```swift
struct AnyAxisMark
```
```

A type-erased axis mark.
```
```swift
```swift
```swift
struct AxisMarkBuilder
```
```

A result builder that constructs axis marks and overrides default marks.
```
```

### [Annotations](/documentation/Charts#Annotations)

```swift
```swift
```swift
```swift
struct AnnotationContext
```
```

Information about an item that you add an annotation to.
```
```swift
```swift
```swift
struct AnnotationPosition
```
```

The position of an annotation.
```
```swift
```swift
```swift
struct AnnotationOverflowResolution
```
```
```
```

### [Data bins](/documentation/Charts#Data-bins)

```swift
```swift
```swift
```swift
struct NumberBins
```
```

A collection of bins for a chart that plots data against numbers.
```
```swift
```swift
```swift
struct DateBins
```
```

A collection of bins for a chart that plots data against dates.
```
```swift
```swift
```swift
struct ChartBinRange
```
```

The range of data that a single bin of a chart represents.
```
```

### [Chart management](/documentation/Charts#Chart-management)

```swift
```swift
```swift
```swift
struct ChartPlotContent
```
```

A view that represents a chart’s plot area.
```
```swift
```swift
```swift
struct ChartProxy
```
```

A proxy that you use to access the scales and plot area of a chart.
```
```

### [Scrolling](/documentation/Charts#Scrolling)

```swift
```swift
```swift
```swift
protocol ChartScrollTargetBehavior
```
```

A type that configures the scroll behavior of charts.
```
```swift
```swift
```swift
struct ChartScrollTargetBehaviorContext
```
```

Contextual information that you can use to determine how to best adjust how charts scroll.
```
```

### [Protocols](/documentation/Charts#Protocols)

```swift
```swift
```swift
```swift
protocol AGChartsDecider
```
```
Beta
```
```swift
```swift
```swift
protocol Chart3DContent
```
```
Beta
```
```swift
```swift
```swift
protocol Chart3DSurfaceStyle
```
```
Beta
```
```swift
```swift
```swift
protocol Chart3DSymbolShape
```
```

A type that can act as a shape for the marks that you add to a chart.

Beta
```
```

### [Structures](/documentation/Charts#Structures)

```swift
```swift
```swift
```swift
struct AnyChart3DSymbolShape
```
```

A type-erased plotting shape.

Beta
```
```swift
```swift
```swift
struct BasicChart3DSurfaceStyle
```
```
Beta
```
```swift
```swift
```swift
struct BasicChart3DSymbolShape
```
```

A basic chart symbol shape.

Beta
```
```swift
```swift
```swift
struct Chart3D
```
```
Beta
```
```swift
```swift
```swift
struct Chart3DCameraPose
```
```
Deprecated
```
```swift
```swift
```swift
struct Chart3DCameraProjection
```
```
Beta
```
```swift
```swift
```swift
struct Chart3DContentBuilder
```
```
Beta
```
```swift
```swift
```swift
struct Chart3DPose
```
```
Beta
```
```swift
```swift
```swift
struct Chart3DRenderingStyle
```
```
Beta
```
```swift
```swift
```swift
struct SurfacePlot
```
```
Beta
```
```