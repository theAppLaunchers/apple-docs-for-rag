*   [Nearby Interaction](/documentation/nearbyinteraction)
*   [NINearbyPeerConfiguration](/documentation/nearbyinteraction/ninearbypeerconfiguration)
*   isCameraAssistanceEnabled

Instance Property

# isCameraAssistanceEnabled

A Boolean value that combines the spatial awareness of ARKit with Nearby Interaction to improve the accuracy of a nearby object’s position.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
var isCameraAssistanceEnabled: [`Bool`](/documentation/Swift/Bool) { get set }
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/NearbyInteraction/NINearbyPeerConfiguration/isCameraAssistanceEnabled#mentions)

[

Initiating and maintaining a session](/documentation/nearbyinteraction/initiating-and-maintaining-a-session)

## [Discussion](/documentation/NearbyInteraction/NINearbyPeerConfiguration/isCameraAssistanceEnabled#Discussion)

The default value is `false`.

When `true`, this property leverages [ARKit](/documentation/ARKit) to provide a nearby object’s [`distance`](/documentation/nearbyinteraction/ninearbyobject/distance-9atp7) and [`direction`](/documentation/nearbyinteraction/ninearbyobject/direction-4qh5w) in a wider range of environmental conditions.

By studying image captures from the device’s camera, ARKit creates an accurate world model of the user’s physical space. As the user moves, ARKit tracks the device with 6 degrees of freedom, by noting the device’s:

*   3D position `(x, y, z)`
    
*   3D orientation `(roll, pitch, yaw)`
    

Nearby Interaction adds readings from the device’s Ultra Wideband Chip to attain a robust position for a nearby object. This also enables the interaction session to provide an object’s [`horizontalAngle`](/documentation/nearbyinteraction/ninearbyobject/horizontalangle-hsg) and [`verticalDirectionEstimate`](/documentation/nearbyinteraction/ninearbyobject/verticaldirectionestimate-swift.property).