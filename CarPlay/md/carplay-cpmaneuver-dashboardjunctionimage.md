

- CarPlay
- CPManeuver
-  dashboardJunctionImage 

Instance Property

# dashboardJunctionImage

An image for the CarPlay dashboard that represents an upcoming junction.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

``` source
var dashboardJunctionImage: UIImage? { get set }
```

## Discussion

Provide a junction image to show more visual details about the maneuver, such as the lane a driver should be in when making a turn.

You use a named image asset to supply variants for both dark and light interface styles, and initialize the image using init(named:). CarPlay then selects the correct image for the current interface style.

Note

The maximum image size is 140 x 100 points. CarPlay scales a larger image to fit while maintaining its aspect ratio.

If you don’t provide a dashboard junction image, CarPlay uses junctionImage.

## See Also

### Providing junction images

var junctionImage: UIImage?

An image that represents an upcoming junction.

