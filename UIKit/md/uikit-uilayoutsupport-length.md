

- UIKit
- UILayoutSupport
-  length 

Instance Property

# length

Provides the length, in points, of the portion of a view controller’s view that is overlaid by translucent or transparent UIKit bars.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
var length: CGFloat { get }
```

**Required**

## Discussion

In iOS 7 and later, a view controller’s view occupies the full height of the screen when there are no opaque UIKit bars (such as opaque navigation or tab bars). To keep your content within the area of a view that is not overlaid by translucent or transparent UIKit bars, employ the topLayoutGuide and bottomLayoutGuide properties in the UIViewController class and take advantage of Auto Layout. Query these properties within your implementation of the UIViewController method viewDidLayoutSubviews().

The guides work as follows:

- The top layout guide indicates the distance, in points, between the top of a view controller’s view and the bottom of the bottommost bar that overlays the view

- The bottom layout guide indicates the distance, in points, between the bottom of a view controller’s view and the top the bar (such as a tab bar) that overlays the view.

If you are not using Auto Layout, you can make use of the length property and perform layout calculations yourself. Refer to the code snippets in the descriptions for the topLayoutGuide and bottomLayoutGuide properties, which explain how to obtain the numbers you need.

