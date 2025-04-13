

- ClockKit
- Deprecated articles and symbols
-  Displaying progress views and gauges 

Article

# Displaying progress views and gauges

Add rich visual data to your SwiftUI complications with progress views and gauges.

## Overview

Progress views provide a visual depiction of progress on a task by showing the task’s percent complete. You can configure progress views as either a circle or a line, and include an optional label and tint color.

Gauges, on the other hand, depict a value within a given range of values. You configure gauges much as you do progress views, but gauges have even more options, including minimum and maximum value labels and color gradients.

### Create a Progress View

To instantiate a ProgressView, call the initializer and pass a value.

```
// A progress view that is 20% complete.
ProgressView(value: 0.2)
```

By default, the progress view takes a value between 0.0 and 1.0, and visually represents the percentage of the task’s completion.

### Customize a Progress View

Customize a progress view by selecting a style, adding labels, and setting a tint color. ProgressView supports linear and circular styles. By default, the SwiftUI selects the style based on the view’s context. However, you can add a `progressViewStyle(_:)` modifier to specify the style.

The following code sets a circular style.

```
// A circular progress view.
ProgressView(value: 0.4)
    .progressViewStyle(CircularProgressViewStyle())
```

The code below sets a linear style.

```
// A linear progress view.
ProgressView(value: 0.6)
    .progressViewStyle(LinearProgressViewStyle())
```

ProgressView also supports a label that describes the task. Pass a closure that returns a View to the progress view’s initializer.

```
// A progress view with an image label.
ProgressView(value: 0.8) {
    Image("coffee_template_small")
        .renderingMode(.template)
        .foregroundColor(.yellow)
}
```

The label appears inside a circular style, and below and to the left of the linear progress bar.

Finally, you can use the `progressViewStyle(_:)` modifier to apply a tint to the progress bar.

```
ProgressView(value: 0.4) {
    Image("coffee_template_small")
        .renderingMode(.template)
        .foregroundColor(.yellow)
}
.progressViewStyle(CircularProgressViewStyle(tint: .green))
```

### Create a Gauge

In many ways, the Gauge is similar to the ProgressView. It supports both a linear and circular style, and you can add a label and tinting. The main difference is that the gauge represents a value within a specified range—not the percent complete. It also has additional options, like labels for the range’s minimum, maximum values, and a label for the current value. Finally, it supports color gradients.

### Customize a Gauge

The following example creates temperature gauge, and then customizes it by adding value labels for the minimum, maximum, and current values. It also assigns a color gradient to the gauge.

```
Gauge(value: 76.0, in: 60.0...85.0) {
    Text("ºF")
} currentValueLabel: {
    Text("76")
} minimumValueLabel: {
    Text("60")
} maximumValueLabel: {
    Text("85")
}
.gaugeStyle(
    CircularGaugeStyle(tint:
        Gradient(colors: [.green, .yellow, .orange, .red])))
```

Note that the gauge doesn’t show the label (`ºF` in this example) when you specify the minimum and maximum value labels.

## See Also

### Articles

Creating complications for your watchOS app

Set up and implement complications for your watchOS app.

Declaring complications for your app

Define the complications that your app supports.

Creating a timeline entry

Package your app-specific data into a template and create a timeline entry for that template.

Loading future timeline events

Preserve battery life and improve performance on the watch by providing a timeline with expected data and updates.

Keeping your complications up to date

Replace or extend the data in your complication’s timeline.

Building complications with SwiftUI

Design the appearance of a graphic complication using SwiftUI.

Adding text to a complication

Use text in SwiftUI complications.

