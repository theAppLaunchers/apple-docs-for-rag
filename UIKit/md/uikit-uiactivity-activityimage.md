

- UIKit
- UIActivity
-  activityImage 

Instance Property

# activityImage

An image that identifies the service to the user.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
var activityImage: UIImage? { get }
```

## Discussion

The default value is `nil`. Subclasses must override this property to return a valid image object that can be presented to the user. The UIActivityViewController object uses this image to generate a button for your service in its UI.

The alpha channel of the image is used as a mask to generate the final image that’s presented to the user. Any color data in the image itself is ignored. Opaque pixels have a gradient applied to them, and this gradient is then laid on top of a standard background. Thus, a completely opaque image would yield a gradient-filled rectangle.

For iPhone and iPod touch, images on iOS 7 should be 60 by 60 points; on earlier versions of iOS, you should use images no larger than 43 by 43 points. For iPad, images on iOS 7 should be 76 by 76 points; on earlier versions of iOS, you should use images no larger than 60 by 60 points. On a device with Retina display, the number of pixels is doubled in each direction.

## See Also

### Getting the activity information

class var activityCategory: UIActivity.Category

The category of the activity, which may be used to group activities in the UI.

enum Category

An enumeration that defines categories of activities.

var activityType: UIActivity.ActivityType?

The type of service being provided.

struct ActivityType

A structure that describes the types of activities for which the system has built-in support.

var activityTitle: String?

A user-readable string that describes the service.

