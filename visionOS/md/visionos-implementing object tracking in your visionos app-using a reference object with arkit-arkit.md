

- visionOS
- Implementing object tracking in your visionOS app
-  Using a reference object with ARKit 

Article

# Using a reference object with ARKit

Import a reference object file and track a real-world object in your visionOS app.

## Overview

You can use reference objects in your visionOS app to track real-world objects in a person’s surroundings. With this capability, you can attach virtual content to those real-world objects to create engaging experiences. For example, with a reference object, you can track a household item and add virtual content to it, like highlighting a part and showing how to fix it.

To create a reference object, first, you obtain a 3D model asset, train a machine learning model with that 3D model asset in Create ML, and then import the resulting reference object file into your app. You can use ARKit to import the reference object file, track objects and handle changes to the scene, and adjust the object-tracking properties.

For more information about creating a reference object file, see Implementing object tracking in your visionOS app.

### Import the reference object file

ARKit offers two methods for importing a reference object file. In the first method, you include the reference object file in your Xcode project, and your app loads it directly from the bundle. In the second, the URL-based loader allows your app to load reference object files from other sources, like a website download. For more information, see Exploring object tracking with ARKit.

You use an ObjectTrackingProvider to track your reference object in a spatial location and receive ObjectAnchor updates. `ObjectTrackingProvider` gets the live position and orientation of the real-world object. To receive this data and begin tracking, configure an ARKitSession.

```
func configureAndRunObjectTracking() async -> ObjectTrackingProvider? {
    let referenceObjects = referenceObjectLoader.enabledReferenceObjects

    guard !referenceObjects.isEmpty else {
        fatalError("No reference objects to start tracking")
    }

    // Run a new provider each time when entering the immersive space.
    let objectTracking = ObjectTrackingProvider(referenceObjects: referenceObjects)
    do {
        // Begin an `ARKitSession` with the provider.
        try await arkitSession.run([objectTracking])
    } catch {
        print("Error: \(error)")
        return nil
    }
    self.objectTracking = objectTracking
    return objectTracking
}
```

### Handle changes in the scene

As your app tracks the reference object file, ARKit sends asynchronous updates when it detects changes in a person’s surroundings. Your app needs to account for those changes and update the scene accordingly. An `anchor` represents the position of your real-world object within Apple Vision Pro. The AnchorUpdate structure provides events about the anchors, including adding a new anchor, removing an anchor, and updates on an anchor’s pose and tracking state. You can place visualizations at those anchors to render content on your real-world objects.

```
Task {
    let objectTracking = await appState.configureAndRunObjectTracking()
    guard let objectTracking else {
        return
    }

    // Wait for object anchor updates.
    for await anchorUpdate in objectTracking.anchorUpdates {
        let anchor = anchorUpdate.anchor
        let referenceObject = anchor.referenceObject

        switch anchorUpdate.event {
        case .added: 
            // The system detects a new object anchor.
            print("Added: \(anchor)")
        case .updated:
            if anchor.isTracked {
                // The update for the detected anchor.
                print("Updated tracked anchor: \(anchor)")
            } else {
                // The system is no longer tracking the object anchor.
                print("Anchor is untracked: \(anchor)")
            }
        case .removed: 
            // The system removed the object anchor.
            print("Removed: \(anchor)")
        }
    }
}
```

### Adjust the object-tracking properties for your app

ARKit offers Entitlements for enhanced platform control to create powerful spatial experiences. Specifically for object tracking, you can use the Object-tracking parameter adjustment key to track more objects with a higher frequency.

Note

The object-tracking properties are adjustable only for Enterprise apps. For more information on the Enterprise program, see Apple Developer Enterprise Program.

To configure the entitlement within your app, select your Xcode project and click the Signing & Capabilities tab. Click the Add Capability button (+), scroll to the Object Tracking Parameter Adjustment option, and double-click it to add it to your app. This creates an entitlement file with the `com.apple.developer.arkit.object-tracking-parameter-adjustment.allow` key.

For more information on how to add capabilities in your app, see Adding capabilities to your app.

Next, you need to configure the parameters. Start by initializing a TrackingConfiguation to configure the object tracking.

```
var trackingConfiguration = ObjectTrackingProvider.TrackingConfiguration()
```

With a tracking configuration in place, you can optimize the detection parameters for your app by adjusting the following properties:

maximumTrackableInstances  
The maximum number of instances that you can track across different object types at the same time.

maximumInstancesPerReferenceObject  
The maximum number of instances of each reference object type. The default value is `1`.

detectionRate  
The frequency for detecting objects to track.

stationaryObjectTrackingRate  
The frequency for tracking an object while it remains stationary.

movingObjectTrackingRate  
The frequency for tracking an object while it’s in motion.

Use `TrackingConfiguration` to adjust the values of these properties in your app.

```
trackingConfiguration.maximumInstancesPerReferenceObject = 2
```

Create an `ObjectTrackingProvider`, configuring both your reference objects and the properties for adjustment.

```
dataProvider = ObjectTrackingProvider(referenceObjects: referenceObjects,
                                      trackingConfiguration: trackingConfiguration)
```

To begin tracking, create an `ARKitSession` with your `ObjectTrackingProvider`.

```
do {
    // Begin an `ARKitSession` with the provider.
    try await arkitSession.run([dataProvider])
} catch {
    print("Error: \(error)")
    return nil
}
```

Note

The object-tracking parameter adjustment key doesn’t allow you to change the maximum of 10 reference objects that the system can detect at once.

## See Also

### Object tracking within an app

Using a reference object with Reality Composer Pro

Import a reference object file to track a real-world object in your visionOS app.

Using a reference object with RealityKit

Import a reference object file to track a real-world object in your visionOS app.

