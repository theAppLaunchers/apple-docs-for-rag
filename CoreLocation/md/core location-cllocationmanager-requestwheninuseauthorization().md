

- Core Location
- CLLocationManager
-  requestWhenInUseAuthorization() 

Instance Method

# requestWhenInUseAuthorization()

Requests the user’s permission to use location services while the app is in use.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.15+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func requestWhenInUseAuthorization()
```

## Discussion

You must call this method or requestAlwaysAuthorization() before you can receive location-related information. You may call requestWhenInUseAuthorization() whenever the current authorization status is not determined (CLAuthorizationStatus.notDetermined).

Important

Your app must be in the foreground to show a location authorization prompt.

This method runs asynchronously and prompts the user to grant permission to the app to use location services. The user prompt contains the text from the NSLocationWhenInUseUsageDescription key in your app `Info.plist` file, and the presence of that key is required when calling this method. The user prompt displays the following options, which determine the authorization your app can receive.

| Option | Authorization |
|----|----|
| Allow While Using App | When In Use authorization that does not expire. |
| Allow Once | Temporary When In Use authorization that expires when the app is no longer in use. |
| Don’t Allow | Denied; no further authorization requests are allowed. |

After the user makes a selection and determines the status, the location manager delivers the results to the delegate’s locationManager(_:didChangeAuthorization:) method. If the initial authorization status is anything other than CLAuthorizationStatus.notDetermined, this method does nothing and doesn’t call the locationManager(_:didChangeAuthorization:) method.

If the user’s choice grants When In Use authorization to your app, your app can start any location service and is eligible to receive the results while it’s in use. If the user’s choice grants temporary When In Use authorization, the authorization expires when the app is no longer in use, reverting to Not Determined status (CLAuthorizationStatus.notDetermined). For information about when an app is considered to be in use, see Choosing the Location Services Authorization to Request.

When your app starts standard location services in the foreground, they continue to run in the background if your app has enabled background location updates in the Capabilities tab of your Xcode project. Attempts to start location updates while your app runs in the background will fail. The system displays a location services indicator in the status bar when your app moves to the background with active location services.

Note

In iOS 16 and later, apps that actively track a user’s location or that have recently enabled Core Location display an indicator in Control Center. Be mindful of battery use and user privacy by monitoring the device’s location only when necessary and when the user expects it.

## Topics

### Related Documentation

Handling location updates in the background

Configure your app to receive location updates when it isn’t running in the foreground.

NSLocationWhenInUseUsageDescription

A message that tells the user why the app is requesting access to the user’s location information while the app is running in the foreground.

## See Also

### Requesting authorization for location services

func requestAlwaysAuthorization()

Requests the user’s permission to use location services regardless of whether the app is in use.

func requestTemporaryFullAccuracyAuthorization(withPurposeKey: String, completion: (((any Error)?) -> Void)?)

Requests permission to temporarily use location services with full accuracy and reports the results to the provided completion handler.

func requestTemporaryFullAccuracyAuthorization(withPurposeKey: String)

Requests permission to temporarily use location services with full accuracy.

var authorizationStatus: CLAuthorizationStatus

The current authorization status for the app.

enum CLAuthorizationStatus

Constants that indicate the app’s authorization to use location services.

NSLocationDefaultAccuracyReduced

A Boolean value that indicates whether the app requests reduced location accuracy by default.

NSLocationAlwaysAndWhenInUseUsageDescription

A message that tells the user why the app is requesting access to the user’s location information at all times.

