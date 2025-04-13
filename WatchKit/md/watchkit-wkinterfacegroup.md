

- WatchKit
-  WKInterfaceGroup 

Class

# WKInterfaceGroup

A container for one or more interface objects.

watchOS 2.0+

``` source
class WKInterfaceGroup
```

## Overview

A WKInterfaceGroup is conceptually similar to a superview in UIKit, in that it handles layout for its contained items. A group arranges items vertically or horizontally within its available space. Groups also have attributes that you can use to configure the precise placement of items within the group. You can also nest groups inside of other groups to manage more complex layouts.

Do not subclass or create instances of this class yourself. Instead, define outlets in your interface controller class and connect them to the corresponding objects in your storyboard file. For example, to refer to a group object in your interface, define a property with the following syntax in your interface controller class:

- Swift
- Objective-C

```
@IBOutlet weak var myGroup: WKInterfaceGroup!
```

```
@property (weak, nonatomic) IBOutlet WKInterfaceGroup* myGroup;
```

During the initialization of your interface controller, WatchKit creates a new instance of this class and assigns it to your outlet. At that point, you can use the object in your outlet to make changes to the group’s configuration.

### Interface Builder Configuration Options

Xcode lets you configure information about your group interface object in your storyboard file. The following table lists the attributes you can configure in your storyboard and their meaning.

| Attribute | Description |
|----|----|
| Layout | The layout direction for items in the group. You can stack items horizontally or vertically, or have them overlap |
| Insets | The amount of space (in points) to insert between the edges of the group and its child elements. Selecting Custom lets you specify different values for the top, bottom, left, and right edges. |
| Spacing | Additional spacing (in points) to include between child elements in the group. The default spacing is 2 points. |
| Background | The background image to display behind the group’s items. You can also set this value programmatically using the setBackgroundImage(_:), setBackgroundImageData(_:), or setBackgroundImageNamed(_:) methods. |
| Mode | The content mode for the group’s background image. Use this option to specify whether the image is scaled or pinned to a particular edge of the group. |
| Animate | A Boolean value indicating whether the background image is animatable. Set the value to Yes to configure the animation parameters, including its duration (in seconds) and whether it starts immediately when the parent interface controller appears onscreen. Animations started at load time run continuously in a loop. |
| Color | The background color for the group.You can also set this value programmatically using the setBackgroundColor(_:) method. |
| Radius | The corner radius to apply to the group’s rectangle. Content inside the group is clipped to the corner radius. If you do not specify a custom value, WatchKit applies a 6-point radius by default. |

### Overlapping Content

In watchOS 4 and later, you can use groups to create overlapping content. Set the group’s Layout attribute in the Attribute inspector to Overlap (see Figure 1 ). The system positions each item in the group based on the item’s alignment attributes.

## Topics

### Setting the Group’s Content

func setBackgroundColor(UIColor?)

Changes the background color for the group container.

func setBackgroundImage(UIImage?)

Changes the background image of the group container to the specified image.

func setBackgroundImageData(Data?)

Changes the background image of the group container to the image in the specified data object.

func setBackgroundImageNamed(String?)

Changes the background image of the group container to the image in the specified resource file.

### Setting the Layout Information

func setCornerRadius(CGFloat)

Changes the radius to use when drawing rounded corners for the group.

func setContentInset(UIEdgeInsets)

Sets the distance between the edges of the group and any contained objects.

## Relationships

### Inherits From

- WKInterfaceObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- WKImageAnimatable

## See Also

### Containers

class WKInterfaceSeparator

An interface object that displays a visual separator within a group.

class WKInterfaceTable

An object that creates and manages the contents of a single-column table interface.

class WKInterfacePicker

An interface element that presents a scrolling list of items for the user to choose from.

