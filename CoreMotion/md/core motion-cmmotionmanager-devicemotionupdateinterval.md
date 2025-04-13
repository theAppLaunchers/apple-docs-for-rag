

- Core Motion
- CMMotionManager
-  deviceMotionUpdateInterval 

Instance Property

# deviceMotionUpdateInterval

The interval, in seconds, for providing device-motion updates to the block handler.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+visionOS 1.0+watchOS 2.0+

``` source
var deviceMotionUpdateInterval: TimeInterval { get set }
```

## Mentioned in 

Getting processed device-motion data

## Discussion

The system supplies device-motion updates to the block handler specified in startDeviceMotionUpdates(to:withHandler:) at regular intervals determined by the value of this property. The interval units are in seconds. The value of this property is capped to minimum and maximum values; the maximum value is determined by the maximum frequency supported by the hardware. If your app is sensitive to the intervals of device-motion data, it should always check the timestamps of the delivered CMDeviceMotion instances to determine the true update interval.

## See Also

### Managing Device Motion Updates

var showsDeviceMovementDisplay: Bool

Controls whether the device-movement display is shown.

func startDeviceMotionUpdates(using: CMAttitudeReferenceFrame, to: OperationQueue, withHandler: CMDeviceMotionHandler)

Starts device-motion updates on an operation queue and using a specified reference frame and block handler.

func startDeviceMotionUpdates(to: OperationQueue, withHandler: CMDeviceMotionHandler)

Starts device-motion updates on an operation queue and using a specified block handler.

func startDeviceMotionUpdates(using: CMAttitudeReferenceFrame)

Starts device-motion updates using a reference frame but without a block handler.

func startDeviceMotionUpdates()

Starts device-motion updates without a block handler.

func stopDeviceMotionUpdates()

Stops device-motion updates.

var deviceMotion: CMDeviceMotion?

The latest sample of device-motion data.

typealias CMDeviceMotionHandler

The type of block callback for handling device-motion data.

