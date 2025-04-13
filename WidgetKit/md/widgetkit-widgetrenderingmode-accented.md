

- WidgetKit
- WidgetRenderingMode
-  accented 

Type Property

# accented

The system divides the widget’s view hierarchy into an accent group and a default group, applying a different color to each group.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+watchOS 9.0+

``` source
static let accented: WidgetRenderingMode
```

## Mentioned in 

Preparing widgets for additional platforms, contexts, and appearances

Developing a WidgetKit strategy

Migrating ClockKit complications to WidgetKit

## Discussion

In watchOS, the system displays accented widget-based complications on many watch faces. For example, when the user selects a color, the Infograph watch face uses white for the default group, and the user-selected color for the accent. However, these colors can change from face to face. In the X-Large watch face, the system applies the selected color to the default group, and colors the accent group white. Other faces use system-defined colors for both groups; for example, the Solar Dial face defines both an accent and a default color, and changes these colors based on the time of day.

When applying the colors, the system treats the widget’s views as if they were template images. It replaces the view’s color — rendering the new colors while preserving the view’s alpha channel.

To control your view’s appearance, add the widgetAccentable(_:) modifier to part of your view’s hierarchy. The system adds that view and all of its subviews to the accent group. It puts all other views in the default group.

```
var body: some View {
    VStack {
        Text("MON")
            .font(.caption)
            .widgetAccentable()
        Text("6")
            .font(.title)
        }
    }
}
```

## See Also

### Rendering modes

static let fullColor: WidgetRenderingMode

The system renders the widget in full color.

static let vibrant: WidgetRenderingMode

The system desaturates the widget, making a monochrome version that it uses to create an adaptive, vibrant effect.

