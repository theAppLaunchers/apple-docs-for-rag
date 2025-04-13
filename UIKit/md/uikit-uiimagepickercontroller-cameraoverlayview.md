

- UIKit
- UIImagePickerController
-  cameraOverlayView 

Instance Property

# cameraOverlayView

The view to display on top of the default image picker interface.

iOS 3.1+iPadOS 3.1+Mac Catalyst 13.1+

``` source
@MainActor
var cameraOverlayView: UIView? { get set }
```

## Discussion

You can use an overlay view to present a custom view hierarchy on top of the default image picker interface. The image picker layers your custom overlay view on top of the other image picker views and positions it relative to the screen coordinates. If you have the default camera controls set to be visible, incorporate transparency into your view, or position it to avoid obscuring the underlying content.

You can access this property only when the source type of the image picker is set to UIImagePickerController.SourceType.camera. Attempting to access this property for other source types results in throwing an invalidArgumentException exception.

## See Also

### Customizing the camera controls

Customizing an image picker controller

Manage user interactions and present custom information when taking pictures by adding an overlay view to your image picker.

var showsCameraControls: Bool

A Boolean value that indicates whether the image picker displays the default camera controls.

var cameraViewTransform: CGAffineTransform

The transform to apply to the camera’s preview image.

