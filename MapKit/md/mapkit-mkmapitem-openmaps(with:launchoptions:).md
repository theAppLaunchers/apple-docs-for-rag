

- MapKit
- MKMapItem
-  openMaps(with:launchOptions:) 

Type Method

# openMaps(with:launchOptions:)

Opens the Maps app and displays the specified map items.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.9+visionOS 1.0+watchOS 2.0+

``` source
class func openMaps(
    with mapItems: [MKMapItem],
    launchOptions: [String : Any]? = nil
) -> Bool
```

## Parameters 

`mapItems`  

An array containing one or more `MKMapItem` objects representing the items you want to display on the map.

`launchOptions`  

Additional information that the Maps app can use to configure the map display. For example, you can use the launch options to specify the visible map region, a 3D perspective, and the map type. For a list of keys you can put into this dictionary, see Launch options dictionary keys.

You may specify `nil` for this parameter.

## Return Value

true if the Maps app successfully opens the maps items, or false if there’s an error.

## Discussion

You use this method to pass one or more map items to the Maps app. For example, you might use this method to ask the Maps app to display location-based search results that your app generates. The Maps app displays pins at each location you specify and uses the contents of each map item object to display additional information.

If you specify the MKLaunchOptionsDirectionsModeKey option in the `launchOptions` dictionary, the `mapItems` array may have no more than two items in it. If the array contains one item, the Maps app generates directions from the user’s location to the location that the map item specifies. If the array contains two items, the Maps app generates directions from the location of the first item to the location of the second item in the array.

If you don’t include the MKLaunchOptionsMapCenterKey and MKLaunchOptionsMapSpanKey keys in your `launchOptions` dictionary, the Maps app constructs a region that encompasses the provided items. It uses this region to set the visible portion of the map.

## See Also

### Launching the Maps app

class func openMaps(with: [MKMapItem], launchOptions: [String : Any]?, completionHandler: ((Bool) -> Void)?)

Opens the Maps app using the specified map items and options.

class func openMaps(with: [MKMapItem], launchOptions: [String : Any]?, from: UIScene?, completionHandler: ((Bool) -> Void)?)

Opens the Maps app from a particular scene using the specified map items and options.

func openInMaps(launchOptions: [String : Any]?) -> Bool

Opens the Maps app and displays the map item.

func openInMaps(launchOptions: [String : Any]?, completionHandler: ((Bool) -> Void)?)

Opens the Maps app and displays the map item.

func openInMaps(launchOptions: [String : Any]?, from: UIScene?, completionHandler: ((Bool) -> Void)?)

Opens the Maps app from a particular scene using the specified options.

