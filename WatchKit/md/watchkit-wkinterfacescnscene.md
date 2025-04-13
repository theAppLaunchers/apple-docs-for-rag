

- WatchKit
-  WKInterfaceSCNScene 

Class

# WKInterfaceSCNScene

An object that lets you manage SceneKit content for display in your app.

watchOS 3.0+

``` source
class WKInterfaceSCNScene
```

## Overview

To provide content for a WKInterfaceSCNScene interface object, assign a SCNScene object to the interface’s scene property. For additional methods and properties for working with SceneKit, see the SCNSceneRenderer protocol, which defines functionality common across all platforms.

Do not subclass or create instances of this class yourself. Instead, drag a SceneKit Scene object from your Object Library and add it to your storyboard. Then define an outlet in your interface controller class and connect it to the SceneKit Scene object. For example, to refer to a scene in your interface, define a property with the following syntax in your interface controller class:

- Swift
- Objective-C

```
@IBOutlet weak var sceneInterface: WKInterfaceSCNScene!
```

```
@property (weak, nonatomic) IBOutlet WKInterfaceSCNScene* sceneInterface;
```

During the initialization of your interface controller, WatchKit creates a new instance of this class and assigns it to your outlet. At that point, you can use the object in your outlet to make changes to the SceneKit scene.

The SceneKit scene in your Watch app must be connected to a WKInterfaceSCNScene outlet in your WatchKit extension for the scene to be visible in your watchOS app’s user interface.

### Interface Builder Attributes

Xcode lets you configure information about your SceneKit Scene in your storyboard file. The following table lists the attributes you can configure in your storyboard and their meaning.

| Attribute | Description |
|----|----|
| Antialiasing | The antialiasing mode used for rendering the scene. You can also set this value programmatically using the antialiasingMode property. |
| Frame Rate | The desired frame rate for the scene’s animation. You can also set this value programmatically using the WKInterfaceSCNScene property. |
| Default Lighting | A checkbox that determines whether SceneKit automatically adds lights to a scene. If unchecked, SceneKit uses only the light sources contained in the scene graph. If checked, SceneKit automatically adds and places an omnidirectional light source when rendering scenes that contain no lights or only contain ambient lights. You can also set this value programmatically using the autoenablesDefaultLighting property. |
| Jitter | A checkbox that determines whether SceneKit applies jittering to reduce aliasing artifacts. Jittering is a process that SceneKit uses to improve the visual quality of a rendered scene. While the scene’s content is still, SceneKit moves the pointOfView location very slightly (by less than a pixel in projected screen space). It then composites images rendered after several such moves to create the final rendered scene, creating an antialiasing effect that smooths the edges of rendered geometry. You can also set this value programmatically using the isJitteringEnabled property. |
| Play | A checkbox that determines whether the scene is animated. If unchecked, SceneKit does not increment the scene time, so animations associated with the scene do not play. You can also set this value programmatically using the isPlaying property. |
| Loop | A checkbox that determines whether SceneKit restarts the scene time after all animations in the scene have played. If checked, SceneKit returns the scene time to zero after all animations associated with the scene have played, causing those animations to repeat; otherwise, SceneKit stops playing the scene when all animations have completed. You can also set this value programmatically using the loops property. |

### Enabling Full Screen Mode

By default, when a watchOS app is running, the system reserves a strip of space across the top of the screen to display the time. The app’s content is only displayed in the area below the time.

In watchOS 4 and later, SpriteKit and SceneKit scenes can fill the full screen. When full screen mode is enabled, the SpriteKit or SceneKit scene extends up, under the time. The system still displays the time in the upper right corner with a gradient behind it, making it clearly visible against the scene.

To enable full screen mode, place a SpriteKit or SceneKit scene as the interface controller’s only content. Then, in the interface controller’s Attribute inspector, enable the Full Screen attribute.

## Topics

### Managing the SceneKit Scene

var antialiasingMode: SCNAntialiasingMode

The antialiasing mode used for rendering the scene.

var preferredFramesPerSecond: Int

The animation frame rate that the interface uses to render its scene.

var scene: SCNScene?

The scene to be displayed.

func snapshot() -> UIImage

Renders the scene to a new image object.

### Initializing for SwiftUI

init()

Creates a SceneKit scene for use in SwiftUI.

Deprecated

## Relationships

### Inherits From

- WKInterfaceObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- SCNSceneRenderer

## See Also

### Graphics and games

class WKInterfaceSKScene

A visual WatchKit element that displays a SpriteKit scene.

