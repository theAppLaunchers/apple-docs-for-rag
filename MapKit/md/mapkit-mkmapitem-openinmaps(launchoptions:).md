

- MapKit
- MKMapItem
-  openInMaps(launchOptions:) 

Instance Method

# openInMaps(launchOptions:)

Opens the Maps app and displays the map item.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.9+visionOS 1.0+watchOS 2.0+

``` source
func openInMaps(launchOptions: [String : Any]? = nil) -> Bool
```

## Parameters 

`launchOptions`  

Additional information that the Maps app can use to configure the map display. For example, you can use the launch options to specify the visible map region and the map type. For a list of keys you can put into this dictionary, see Launch options dictionary keys.

This parameter may be `nil`.

## Return Value

true if the Maps app successfully opens the map item, or false if there’s an error.

## Discussion

You use this method to pass the map item to the Maps app. If your map item contains descriptive information about the location (such as a name or URL), the Maps app displays that information at the specified coordinate.

If you specify the MKLaunchOptionsDirectionsModeKey option in the `launchOptions` dictionary, the Maps app interprets that as an attempt to map from the user’s current location to the location that the map item specifies.

Note

This is a blocking call and the system suspends interaction with your app until the Maps app finishes launching.

If you don’t include the MKLaunchOptionsMapCenterKey and MKLaunchOptionsMapSpanKey keys in your `launchOptions` dictionary, the Maps app constructs a region around the map item. It uses that region to set the visible portion of the map.

## See Also

### Launching the Maps app

class func openMaps(with: [MKMapItem], launchOptions: [String : Any]?) -> Bool

Opens the Maps app and displays the specified map items.

class func openMaps(with: [MKMapItem], launchOptions: [String : Any]?, completionHandler: ((Bool) -> Void)?)

Opens the Maps app using the specified map items and options.

class func openMaps(with: [MKMapItem], launchOptions: [String : Any]?, from: UIScene?, completionHandler: ((Bool) -> Void)?)

Opens the Maps app from a particular scene using the specified map items and options.

func openInMaps(launchOptions: [String : Any]?, completionHandler: ((Bool) -> Void)?)

Opens the Maps app and displays the map item.

func openInMaps(launchOptions: [String : Any]?, from: UIScene?, completionHandler: ((Bool) -> Void)?)

Opens the Maps app from a particular scene using the specified options.

