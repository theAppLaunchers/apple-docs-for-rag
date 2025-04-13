

- ClockKit
- Deprecated articles and symbols
-  Building complications with SwiftUI 

Article

# Building complications with SwiftUI

Design the appearance of a graphic complication using SwiftUI.

## Overview

ClockKit provides SwiftUI templates for all of the graphic complication families. These templates use a View instance to define some or all of the complication’s content. To access these templates, import both ClockKit and SwiftUI.

```
import ClockKit
import SwiftUI
```

ClockKit provides a variety of templates for each family. Many of these mix SwiftUI views with other data providers. However, some templates take only a single SwiftUI view.

- CLKComplicationTemplateGraphicCircularView

- CLKComplicationTemplateGraphicRectangularFullView

- CLKComplicationTemplateGraphicExtraLargeCircularView

These templates provide a blank canvas that you can use to draw the entire complication.

### Present a View

ClockKit varies the SwiftUI view’s size based on the template. The SwiftUI template replaces a full color image provider with a SwiftUI view. The view has the same dimensions as the corresponding image.

Also, the template may mask the SwiftUI view to a circle or apply a corner radius to the view, just as it does for the full color images. In particular, the CLKComplicationTemplateGraphicRectangularFullView template provides the full graphic rectangular complication as a single SwiftUI view. This view is 162 pt x 69 pt on the 40 mm Apple Watch, and 184 pt x 78 pt on the 44 mm watch, but the template provides a safe area inset to help you avoid clipping your content. Use the edgesIgnoringSafeArea(_:) modifier, if you need to fill the complication to the edges.

For additional details, see each template’s class reference document.

### Design a View

Use SwiftUI static views, such as text, shapes, or images, to create your complication’s content. You can also add render effects like blurs and gradients, but keep in mind that complications only have one or two frames in which to render the effect.

Because complications show a snapshot of the apps data at a particular point in time, they don’t support features like animation. Additionally, if the user touches your complication, the system launches your app instead of passing the touch event to the SwiftUI views, so a complication can’t use interactive elements like buttons or switches.

### Support Tinted Views

Some watch faces let the user select a tint color that affects how the face displays graphical complications. Some watch faces use a complex set of colors; for example, the Solar Dial face sets both a foreground and background color, and the colors change based on the time of day.

By default, when ClockKit displays your complication on a tinted watch face, it desaturates your SwiftUI view to create a grayscale version. For some faces, like the California face, it then applies a single tint color to the desaturated view.

To control how the system tints your view, divide your view hierarchy into two layers, a foreground layer and the background layer. ClockKit looks at the opacity of each layer when applying the tint.

For most watch faces, ClockKit applies the user-selected tint color to one layer, and a system-defined color to the other. For example, the Infograph watch face applies white to the background and the user-selected tint to the foreground. However, the foreground and background colors can change from face to face. in the X-Large watch face, ClockKit applies white to the foreground, and the tint color to the background. On other faces, like Solar Dial, it applies system-defined colors to both layers.

To divide your view into layers, add the complicationForeground() modifier to part of your view hierarchy. That view and all of its subviews become the foreground layer. Everything else is in the background layer.

```
ZStack {
    Rectangle()
        .fill(Color.purple)
    Image("coffee_template")
        .renderingMode(.template)
        .resizable()
        .aspectRatio(contentMode: .fit)
        .foregroundColor(.yellow)
        .complicationForeground()
}
```

For even greater control, you can check the complication’s rendering mode, and then change the design based on whether the system displays the face in a full color or a tinted mode. You can access the current ComplicationRenderingMode value from the Environment.

```
@Environment(\.complicationRenderingMode) var renderingMode

var body: some View {
    ZStack {

        if renderingMode == .fullColor {
            Circle()
                .fill(Color.purple)
        } else {
            Circle()
                .fill(LinearGradient(
                        gradient: Gradient(
                            colors: [Color.white.opacity(0.3),
                                     Color.white.opacity(1.0)]),
                        startPoint: .top,
                        endPoint: .bottom))
        }

        Image("coffee_template")
            .renderingMode(.template)
            .resizable()
            .aspectRatio(contentMode: .fit)
            .foregroundColor(.yellow)
            .complicationForeground()
    }
}
```

In this example, if the system renders the watch face in ComplicationRenderingMode.fullColor mode, it uses a solid blue circle as the background. However, if the system renders the face in ComplicationRenderingMode.tinted mode, it uses a gradient fill. For a tinted complication, the selected color has no effect; the system only looks at the opacity, and then applies its own color.

### Preview the Complication

Like other SwiftUI views, you can preview your complications as you design them. To enable previews:

1.  Add a PreviewProvider to the bottom of your complication controller’s file.

2.  In the previews property, instantiate your template, and call its `previewContext(faceColor:)` method.

Calling `previewContext()` with no argument defaults to a full-color watch face. To preview a tinted watch face, pass the desired tint color to the `faceColor` parameter. Use a `Group` to preview multiple complications at once.

```
struct ComplicationController_Previews: PreviewProvider {
    static var previews: some View {
        Group {

            CLKComplicationTemplateGraphicExtraLargeCircularView(MyCoffeeView()).previewContext()

            CLKComplicationTemplateGraphicExtraLargeCircularView(MyCoffeeView()).previewContext(faceColor: .red)
        }
    }
}
```

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

Displaying progress views and gauges

Add rich visual data to your SwiftUI complications with progress views and gauges.

Adding text to a complication

Use text in SwiftUI complications.

