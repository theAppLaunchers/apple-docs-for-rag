

- Core Location
- CLLocationManager
-  startMonitoringSignificantLocationChanges() 

Instance Method

# startMonitoringSignificantLocationChanges()

Starts the generation of updates based on significant location changes.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+

``` source
func startMonitoringSignificantLocationChanges()
```

## Mentioned in 

Getting the current location of a device

## Discussion

This method initiates the delivery of location events asynchronously, returning shortly after you call it. Location events are delivered to your delegate’s locationManager(_:didUpdateLocations:) method. The first event to be delivered is usually the most recently cached location event (if any) but may be a newer event in some circumstances. Obtaining a current location fix may take several additional seconds, so be sure to check the timestamps on the location events in your delegate method.

After returning a current location fix, the receiver generates update events only when a significant change in the user’s location is detected. It does not rely on the value in the distanceFilter property to generate events. Calling this method several times in succession does not automatically result in new events being generated. Calling stopMonitoringSignificantLocationChanges() in between, however, does cause a new initial event to be sent the next time you call this method.

If you start this service and your app is subsequently terminated, the system automatically relaunches the app into the background if a new event arrives. In such a case, the options dictionary passed to the application(_:willFinishLaunchingWithOptions:) and application(_:didFinishLaunchingWithOptions:) methods of your app delegate contains the key location to indicate that your app was launched because of a location event. Upon relaunch, you must still configure a location manager object and call this method to continue receiving location events. When you restart location services, the current event is delivered to your delegate immediately. In addition, the location property of your location manager object is populated with the most recent location object even before you start location services.

In addition to your delegate object implementing the locationManager(_:didUpdateLocations:) method, it should also implement the locationManager(_:didFailWithError:) method to respond to potential errors.

Note

Apps can expect a notification as soon as the device moves 500 meters or more from its previous notification. It should not expect notifications more frequently than once every five minutes. If the device is able to retrieve data from the network, the location manager is much more likely to deliver notifications in a timely manner.

If a compatible iPad or iPhone app calls this method when running in visionOS, the method does nothing.

## See Also

### Running the significant change location service

func stopMonitoringSignificantLocationChanges()

Stops the delivery of location events based on significant location changes.

