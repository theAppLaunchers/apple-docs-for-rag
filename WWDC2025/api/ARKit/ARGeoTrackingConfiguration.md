*   [ARKit](/documentation/arkit)
*   ARGeoTrackingConfiguration

Class

# ARGeoTrackingConfiguration

A configuration that tracks locations with GPS, map data, and a device’s compass.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class ARGeoTrackingConfiguration
```
```
```
```
```
```
```
```

## [Overview](/documentation/ARKit/ARGeoTrackingConfiguration#overview)

This configuration creates location anchors ([`ARGeoAnchor`](/documentation/arkit/argeoanchor)) that specify a particular latitude, longitude, and optionally, altitude to enable an app to track geographic areas of interest in an AR experience.

Important

The [`isSupported`](/documentation/arkit/arconfiguration/issupported) property returns [`true`](/documentation/swift/true) for this class on iOS 14 & iPadOS 14 devices that have an A12 chip or later and cellular (GPS) capability. Geotracking is available in specific geographic locations. To determine availability at the user’s location at runtime, call [`checkAvailability(completionHandler:)`](/documentation/arkit/argeotrackingconfiguration/checkavailability\(completionhandler:\)).

Geotracking occurs exclusively outdoors. If a geotracking app navigates users between waypoints, your app needs to handle any events along a route. The user must have an internet connection, and you can provide them information about data usage, as described in [`ARGeoAnchor`](/documentation/arkit/argeoanchor).

### [Encourage user safety](/documentation/ARKit/ARGeoTrackingConfiguration#Encourage-user-safety)

To keep your users’ focus on the road while traveling, discourage them from looking at the device when in motion, such as while riding a bike. Keep users informed when navigating through unfamiliar territory. For instance, you can recommend they steer clear of private property, or remind them to check their device’s battery level before beginning a long route.

### [Refine the user’s position with imagery](/documentation/ARKit/ARGeoTrackingConfiguration#Refine-the-users-position-with-imagery)

To place location anchors with precision, geotracking requires a better understanding of the user’s geographic location than is possible with GPS alone. Based on the user’s GPS coordinates, ARKit downloads imagery that depicts the physical environment in that area. Apple collects this _localization imagery_ in advance by capturing photos of the view from the street and recording the geographic position at each photo. By comparing the device’s current camera image with this imagery, the session matches the user’s precise geographic location with the scene’s local coordinates. For information about the user’s position in local space, see [`transform`](/documentation/arkit/arcamera/transform).

Localization imagery captures views from public streets and routes accessible by car, but doesn’t include images of gated or pedestrian-only areas.

Geotracking sessions use localization imagery in the [`ARGeoTrackingStatus.State.localizing`](/documentation/arkit/argeotrackingstatus/state-swift.enum/localizing) state.

### [Supported areas and cities](/documentation/ARKit/ARGeoTrackingConfiguration#Supported-areas-and-cities)

Localization imagery is available for specific areas in over 20 countries, including many metropolitan areas in Australia, Europe, Japan, and North America. To check availability in a particular location, see the [`checkAvailability(completionHandler:)`](/documentation/arkit/argeotrackingconfiguration/checkavailability\(completionhandler:\)) function.

Tip

You can share an experience of geotracking with developers who live outside an area that supports it. Record a session in your app in an area that supports localization imagery for developers to create and test their geotracking app. For more information, see [Recording and Replaying AR Session Data](/documentation/arkit/recording-and-replaying-ar-session-data).

## [Topics](/documentation/ARKit/ARGeoTrackingConfiguration#topics)

### [Creating a configuration](/documentation/ARKit/ARGeoTrackingConfiguration#Creating-a-configuration)

[`init()`](/documentation/arkit/argeotrackingconfiguration/init\(\))

Initializes a new geotracking configuration.

### [Checking availability](/documentation/ARKit/ARGeoTrackingConfiguration#Checking-availability)

```swift
```swift
```swift
```swift
class func checkAvailability(completionHandler: (Bool, (any Error)?) -> Void)
```
```

Determines if geotracking supports the user’s current location.
```
```swift
```swift
```swift
class func checkAvailability(at: CLLocationCoordinate2D, completionHandler: (Bool, (any Error)?) -> Void)
```
```

Determines if geotracking supports a particular location.
```
```

### [Tracking surfaces](/documentation/ARKit/ARGeoTrackingConfiguration#Tracking-surfaces)

```swift
```swift
```swift
```swift
var planeDetection: ARWorldTrackingConfiguration.PlaneDetection
```
```

A value that specifies whether and how the session automatically attempts to detect flat surfaces in the camera-captured image.
```
```swift
```swift
```swift
struct PlaneDetection
```
```

Options for whether and how the framework detects flat surfaces in captured images.
```
```

### [Detecting or tracking images](/documentation/ARKit/ARGeoTrackingConfiguration#Detecting-or-tracking-images)

```swift
```swift
```swift
```swift
var detectionImages: Set<ARReferenceImage>!
```
```

A set of images that ARKit searches for in the user’s environment.
```
```swift
```swift
```swift
var maximumNumberOfTrackedImages: Int
```
```

The number of image anchors to monitor closely for position and orientation updates.
```
```swift
```swift
```swift
var automaticImageScaleEstimationEnabled: Bool
```
```

A flag that instructs the framework to estimate and set the scale of a detected or tracked image on your behalf.
```
```

### [Detecting real-world objects](/documentation/ARKit/ARGeoTrackingConfiguration#Detecting-real-world-objects)

```swift
```swift
```swift
```swift
var detectionObjects: Set<ARReferenceObject>
```
```

A set of 3D objects that the framework attempts to detect in the user’s environment.
```
```

### [Creating realistic reflections](/documentation/ARKit/ARGeoTrackingConfiguration#Creating-realistic-reflections)

```swift
```swift
```swift
```swift
var environmentTexturing: ARWorldTrackingConfiguration.EnvironmentTexturing
```
```

An option that determines how the framework generates environment textures.
```
```swift
```swift
```swift
enum EnvironmentTexturing
```
```

The available environment texturing options for world tracking.
```
```swift
```swift
```swift
class AREnvironmentProbeAnchor
```
```

An object that provides environmental lighting information for a specific area of space in a world-tracking AR session.
```
```swift
```swift
```swift
var wantsHDREnvironmentTextures: Bool
```
```

A flag that instructs the framework to create environment textures in HDR format.
```
```

### [Accessing app clip codes](/documentation/ARKit/ARGeoTrackingConfiguration#Accessing-app-clip-codes)

[

Interacting with App Clip Codes in AR](/documentation/AppClip/interacting-with-app-clip-codes-in-ar)

Display content and provide services in an AR experience with App Clip Codes.

```swift
```swift
```swift
class var supportsAppClipCodeTracking: Bool
```
```

A flag that indicates if the device tracks App Clip Codes.
```
```swift
```swift
```swift
var appClipCodeTrackingEnabled: Bool
```
```

A Boolean value that indicates if the framework searches the physical environment for App Clip Codes.
```
```swift
```swift
```swift
class ARAppClipCodeAnchor
```
```

An anchor that tracks the position and orientation of an App Clip Code in the physical environment.
```

## [Relationships](/documentation/ARKit/ARGeoTrackingConfiguration#relationships)

### [Inherits From](/documentation/ARKit/ARGeoTrackingConfiguration#inherits-from)

*   [`ARConfiguration`](/documentation/arkit/arconfiguration)

### [Conforms To](/documentation/ARKit/ARGeoTrackingConfiguration#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCopying`](/documentation/Foundation/NSCopying)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/ARKit/ARGeoTrackingConfiguration#see-also)

### [Spatial Tracking](/documentation/ARKit/ARGeoTrackingConfiguration#Spatial-Tracking)

[

Understanding World Tracking](/documentation/arkit/understanding-world-tracking)

Discover features and best practices for building rear-camera AR experiences.

```swift
```swift
```swift
class ARWorldTrackingConfiguration
```
```

A configuration that tracks the position of a device in relation to objects in the environment.
```
```swift
```swift
```swift
class AROrientationTrackingConfiguration
```
```

A configuration that tracks only the device’s orientation using the rear-facing camera.
```
```swift
```swift
```swift
class ARPositionalTrackingConfiguration
```
```

A configuration that tracks only the device’s position in 3D space.
```