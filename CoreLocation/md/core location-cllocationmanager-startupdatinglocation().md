

- Core Location
- CLLocationManager
-  startUpdatingLocation() 

Instance Method

# startUpdatingLocation()

Starts the generation of updates that report the user’s current location.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.6+visionOS 1.0+watchOS 3.0+

``` source
func startUpdatingLocation()
```

## Mentioned in 

Getting the current location of a device

## Discussion

This method returns immediately. Calling this method causes the location manager to obtain an initial location fix (which may take several seconds) and notify your delegate by calling its locationManager(_:didUpdateLocations:) method. After that, the receiver generates update events primarily when the value in the distanceFilter property is exceeded. Updates may be delivered in other situations though. For example, the receiver may send another notification if the hardware gathers a more accurate location reading.

Calling this method several times in succession does not automatically result in new events being generated. Calling stopUpdatingLocation() in between, however, does cause a new initial event to be sent the next time you call this method.

If you start this service and your app is suspended, the system stops the delivery of events until your app starts running again (either in the foreground or background). If your app is terminated, the delivery of new location events stops altogether. Therefore, if your app needs to receive location events while in the background, it must include the `UIBackgroundModes` key (with the `location` value) in its `Info.plist` file.

In addition to your delegate object implementing the locationManager(_:didUpdateLocations:) method, it should also implement the locationManager(_:didFailWithError:) method to respond to potential errors.

## See Also

### Running the standard location service

func stopUpdatingLocation()

Stops the generation of location updates.

func requestLocation()

Requests the one-time delivery of the user’s current location.

var pausesLocationUpdatesAutomatically: Bool

A Boolean value that indicates whether the location-manager object may pause location updates.

var allowsBackgroundLocationUpdates: Bool

A Boolean value that indicates whether the app receives location updates when running in the background.

var showsBackgroundLocationIndicator: Bool

A Boolean value that indicates whether the status bar changes its appearance when an app uses location services in the background.

var activityType: CLActivityType

The type of activity the app expects the user to typically perform while in the app’s location session.

enum CLActivityType

Constants that indicate the type of activity associated with location updates.

