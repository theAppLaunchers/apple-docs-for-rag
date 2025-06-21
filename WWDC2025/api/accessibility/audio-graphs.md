Collection

*   [Accessibility](/documentation/accessibility)
*   [Accessibility API](/documentation/accessibility/accessibility-api)
*   Audio graphs

API Collection

# Audio graphs

Define an accessible representation of your chart for VoiceOver to generate an audio graph.

## [Overview](/documentation/Accessibility/audio-graphs#overview)

Charts and graphs help users quickly identify important features and trends in data. Use the audio graphs API to provide all the information that VoiceOver needs to construct an audible representation of the data in your charts and graphs, making the data accessible to people who are blind or have low vision.

![An illustration of an audio graph that shows data points modulating in pitch along the y-axis as a slider moves in time along the x-axis.](https://docs-assets.developer.apple.com/published/ff287c418eb62bd9916511190687db82/audio_graphs-1%402x.png)

An _audio graph_ turns the data in your chart into an audible representation by encoding the data on each axis as audio. Typically, the audio graph represents the x-axis as time, and the y-axis as pitch. For example, an audible representation of a scatter plot that shows a linear downward trend might be a series of individual tones descending in pitch over time. An audible representation of a stock chart might be a single continuous tone with a pitch that modulates up or down with the stock price (y-axis) as the audio plays over time (x-axis).

Related sessions from WWDC21

Session 10122: [Bring accessibility to charts in your app](https://developer.apple.com/wwdc21/10122)

## [Topics](/documentation/Accessibility/audio-graphs#topics)

### [Essentials](/documentation/Accessibility/audio-graphs#Essentials)

[

Representing chart data as an audio graph](/documentation/accessibility/representing-chart-data-as-an-audio-graph)

Define accessible representations of your chart’s components for VoiceOver to construct an audible representation of the data.

### [Chart representation](/documentation/Accessibility/audio-graphs#Chart-representation)

```swift
```swift
```swift
```swift
protocol AXChart
```
```

A protocol that declares the minimum interface necessary for an accessibility element to act as a chart.
```
```swift
```swift
```swift
class AXChartDescriptor
```
```

An object that contains all the semantic information about an accessible chart.
```
```

### [Axis representation](/documentation/Accessibility/audio-graphs#Axis-representation)

```swift
```swift
```swift
```swift
protocol AXDataAxisDescriptor
```
```

The basic interface for a data axis in a chart.
```
```swift
```swift
```swift
class AXCategoricalDataAxisDescriptor
```
```

An object that represents an axis of categorical data.
```
```swift
```swift
```swift
class AXNumericDataAxisDescriptor
```
```

An object that represents an axis of numerical data.
```
```

### [Data representation](/documentation/Accessibility/audio-graphs#Data-representation)

```swift
```swift
```swift
```swift
class AXDataPoint
```
```

An object that represents a single data point in a chart.
```
```swift
```swift
```swift
class AXDataSeriesDescriptor
```
```

An object that represents a series of data points.
```
```

### [Live audio graphs](/documentation/Accessibility/audio-graphs#Live-audio-graphs)

```swift
```swift
```swift
```swift
class AXLiveAudioGraph
```
```

An object that represents an audio graph for a live-updating, continuous data series for VoiceOver.
```
```

## [See Also](/documentation/Accessibility/audio-graphs#see-also)

### [Features](/documentation/Accessibility/audio-graphs#Features)

[

API Reference

Customized accessibility content](/documentation/accessibility/customized-accessibility-content)

Customize your apps to deliver accessibility information to your users in measured portions as they need it.

[

API Reference

Braille displays](/documentation/accessibility/braille-displays)

Display a graphical representation of images, icons, data, and more on a two-dimensional braille display.

[

API Reference

Hearing device support](/documentation/accessibility/hearing-device-support)

Access information about paired hearing aid devices and streaming status.

```swift
```swift
```swift
func AXNameFromColor(CGColor) -> String
```
```

Returns a localized description of the color to use in accessibility attributes.
```