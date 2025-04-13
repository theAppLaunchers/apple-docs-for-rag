

- UIKit
- Drawing
- UIColor
-  Customizing drawings 

Article

# Customizing drawings

Create custom colors and patterns for drawing in your app.

## Overview

You can customize the colors in your app, including the background and tint colors and the drawing styles available to users of your app.

### Set custom background and tint colors

The most common way to use a UIColor object is to include it with some other object in UIKit. Including UIColor with an object in UIKit allows you to create and customize the UI of your app. For example, the UIView class (and its descendants) includes background and tint colors to affect how they’re drawn onscreen. The following code example sets the background and tint color of a view.

```
backgroundView.backgroundColor = UIColor.systemGray
backgroundView.tintColor = UIColor.systemBlue
```

### Create custom colors and drawing styles

When customizing drawings in your app, a UIColor object provides methods that set the fill or stroke colors of the current graphics context. These methods can set the color of an object and create various patterns and styles. The following code shows a simple example of a custom drawing inside a view.

```
class CircleView: UIView {

    override func draw(_ rect: CGRect) {
        let ovalBounds = self.bounds.insetBy(dx: 10, dy: 10)
        let oval = UIBezierPath(ovalIn: ovalBounds)
        let brightRed = UIColor(displayP3Red: 1.0, green: 0.0, blue: 0.0, alpha: 1.0)
        brightRed.setFill()
        oval.fill()
    }
}
```

## See Also

### Applying the color to the drawing environment

func set()

Sets the color of subsequent stroke and fill operations to the color that the receiver represents.

func setFill()

Sets the color of subsequent fill operations to the color that the receiver represents.

func setStroke()

Sets the color of subsequent stroke operations to the color that the receiver represents.

