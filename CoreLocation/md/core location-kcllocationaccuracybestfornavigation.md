

- Core Location
-  kCLLocationAccuracyBestForNavigation 

Global Variable

# kCLLocationAccuracyBestForNavigation

The highest possible accuracy that uses additional sensor data to facilitate navigation apps.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
let kCLLocationAccuracyBestForNavigation: CLLocationAccuracy
```

## Discussion

This level of accuracy is intended for use in navigation apps that require precise position information at all times. Because of the extra power requirements, use this level of accuracy only while the device is plugged in.

This level of accurate is available only if `isAuthorizedForPreciseLocation` is true.

## See Also

### Desired Accuracy Constants

let kCLLocationAccuracyBest: CLLocationAccuracy

The best level of accuracy available.

let kCLLocationAccuracyNearestTenMeters: CLLocationAccuracy

Accurate to within ten meters of the desired target.

let kCLLocationAccuracyHundredMeters: CLLocationAccuracy

Accurate to within one hundred meters.

let kCLLocationAccuracyKilometer: CLLocationAccuracy

Accurate to the nearest kilometer.

let kCLLocationAccuracyThreeKilometers: CLLocationAccuracy

Accurate to the nearest three kilometers.

let kCLLocationAccuracyReduced: CLLocationAccuracy

The level of accuracy used when an app isn’t authorized for full accuracy location data.

