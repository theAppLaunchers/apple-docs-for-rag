Framework

# RoomPlan

Create a 3D model of a room by interactively guiding people to scan their physical environment using a device’s camera.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+

## [Overview](/documentation/RoomPlan#Overview)

Use RoomPlan to create a 3D model of an interior room. The framework uses a device’s sensors, trained ML models, and RealityKit’s rendering capabilities to capture the physical surroundings of an interior room. For example, the framework inspects a device’s camera feed and LiDAR readings to identify walls, windows, openings, and doors. RoomPlan also recognizes room features, furniture, and appliances, such as a fireplace, bed, or refrigerator, and provides that information to the app.

To begin a capture, the app presents a view ([`RoomCaptureView`](/documentation/roomplan/roomcaptureview)) that the user looks through to see their room in AR. The view displays virtual cues as they move around the room:

*   Real-time graphic overlays display on top of physical structures in the room to convey scanning progress.
    
*   If the framework requires a specific kind of device movement or perspective to complete the capture, the UI displays instructions that explain how to position the device.
    

![An illustration of a hand holding an iPhone in portrait mode in a kitchen. The device’s screen displays a camera feed of the kitchen with highlights around physical structures, such as the window and the sink. At the top of the screen is a banner that reads Move device to start. To the right of that banner is a callout that reads Instructional text. Another callout to the right of the device’s screen reads Structural highlights and points to the highlight around the window.](https://docs-assets.developer.apple.com/published/78ae1d75bc69bde0b0dee238d672cf6a/roomplan-hero-1%402x.png)

When the app determines that the current scan is complete, the view displays a small-scale version of the scanned room for the user to approve.

Alternatively, your app can display custom graphics during the scanning process by creating and using a scan session object ([`RoomCaptureSession`](/documentation/roomplan/roomcapturesession)) directly.

### [Access the captured results](/documentation/RoomPlan#Access-the-captured-results)

The framework outputs a scan as _parametric_ data, which makes it easy for your app to modify the scanned room’s individual components. RoomPlan also provides the results in various Universal Scene Description (USD) formats. With these assets, your app can implement custom features, such as the following:

*   Estimate the size of particular areas of a room.
    
*   Preview virtual furniture from a catalog in a variety of styles and positions.
    
*   Integrate a version of a scanned room or structure in a 3D game.
    

![An illustration of a scanned room showing its data representations. From the left, the illustration shows a small scale 3D version of a scanned room. Three arrows flow to the right. The top arrow points to a house icon and four 2D images of floor plans with rulers that measure objects in the floor plans. The middle arrow points to an icon of a shopping cart and an iPhone in portrait mode that displays a furniture catalog with tables, a lamp, and chairs. Next to the phone is a copy of the small scale 3D version of a scanned room that includes a highlighted virtual table from the catalog. The bottom arrow points to an icon of a game controller and an iPhone in landscape mode that displays a 3D game version of the scanned room.](https://docs-assets.developer.apple.com/published/8909a2da99ac2c9fbb690113e0b340ed/roomplan-hero-2%402x.png)

### [Process scan results on macOS with Mac Catalyst](/documentation/RoomPlan#Process-scan-results-on-macOS-with-Mac-Catalyst)

Mac apps built with Mac Catalyst can access [`CapturedRoom`](/documentation/roomplan/capturedroom) and [`CapturedStructure`](/documentation/roomplan/capturedstructure) and can perform encoding, decoding, and exporting. Environment scanning relies on a camera, LiDAR, and other sensors that support augmented reality on iOS and iPad OS devices. However, macOS apps built with Mac Catalyst can process the results of room-capture sessions performed on those devices. RoomPlan ignores all capture-session-related calls on macOS apps built with Mac Catalyst.

## [Topics](/documentation/RoomPlan#topics)

### [Essentials](/documentation/RoomPlan#Essentials)

[

Create a 3D model of an interior room by guiding the user through an AR experience](/documentation/roomplan/create-a-3d-model-of-an-interior-room-by-guiding-the-user-through-an-ar-experience)

Highlight physical structures and display text that guides a user to scan the shape of their physical environment using a framework-provided view.

### [User Interface](/documentation/RoomPlan#User-Interface)

```swift
```swift
```swift
```swift
class RoomCaptureView
```
```

A view that enables the user to scan their room with the device’s camera.
```
```swift
```swift
```swift
protocol RoomCaptureViewDelegate
```
```

A specification to post-process the results of a scan.
```
```

### [Scanning Protocol](/documentation/RoomPlan#Scanning-Protocol)

```swift
```swift
```swift
```swift
class RoomCaptureSession
```
```

An object that manages the room-scanning process.
```
```swift
```swift
```swift
protocol RoomCaptureSessionDelegate
```
```

A specification of important events in the room-scanning process.
```
```

### [Captured Data](/documentation/RoomPlan#Captured-Data)

[

Merging multiple scans into a single structure](/documentation/roomplan/merging-multiple-scans-into-a-single-structure)

Export a 3D model that consists of multiple rooms captured in the same physical vicinity.

[

Scanning the rooms of a single structure](/documentation/roomplan/scanning-the-rooms-of-a-single-structure)

Create an AR experience that enables people to scan a building that contains multiple rooms.

```swift
```swift
```swift
struct CapturedRoom
```
```

A structure that provides the key details of a scanned room.
```
```swift
```swift
```swift
struct CapturedStructure
```
```

An object that holds the results of the merger of multiple capture sessions.
```
```swift
```swift
```swift
struct CapturedRoomData
```
```

An opaque object that holds the raw results of a scan.
```

[

API Reference

Captured Object Attributes](/documentation/roomplan/captured-object-attributes)

Determine details about the objects and surfaces that the framework identifies in a scan.

### [3D Asset Output](/documentation/RoomPlan#3D-Asset-Output)

[

Providing custom models for captured rooms and structure exports](/documentation/roomplan/providing-custom-models-for-captured-rooms-and-structure-exports)

Enhance the look of an exported 3D model by substituting object bounding boxes with detailed 3D renditions.

```swift
```swift
```swift
class RoomBuilder
```
```

An object that generates a 3D asset from room-capture data.
```
```swift
```swift
```swift
class StructureBuilder
```
```

An object that combines multiple scan sessions into a single captured result.
```
```swift
```swift
```swift
struct USDExportOptions
```
```

Options that determine the underlying data format of a scan export.
```