

- Media Player
- MPMoviePlayerController
-  view Deprecated

Instance Property

# view

The view containing the movie content and controls.

iOS 3.2–9.0DeprecatediPadOS 3.2–9.0DeprecatedMac Catalyst 13.1–13.1Deprecated

``` source
var view: UIView! { get }
```

Deprecated

Use AVPlayerViewController in AVKit

## Discussion

This property contains the view used for presenting the video content. This view incorporates all the background, content, and controls needed to display movies. You can incorporate this view into your own view hierarchies or present it by itself using a view controller.

To embed the view into your own view hierarchies, add it as a subview to one of your existing views. A good place to do this is in the loadView() or viewDidLoad() method of the custom view controller that presents your view hierarchy. You are free to change the view’s frame rectangle to accommodate the space available in your view hierarchy. The movie player uses the value in the scalingMode property to scale the movie content to match the frame you specify.

If you want to present the view by itself—that is, without embedding it in an existing view hierarchy—you can use an instance of the MPMoviePlayerViewController class to manage the presentation of the view. That class works directly with the movie player controller to present the view by itself.

You can add subviews to the view in this property. You might do this in cases where you want to display custom playback controls or add other custom content that is relevant to your app.

## See Also

### Accessing the view

var backgroundView: UIView!

A customizable view that is displayed behind the movie content.

Deprecated

