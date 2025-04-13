

- WatchKit
- Storyboard support
- WKInterfaceSKScene
-  Configuring a WatchKit Scene in a Storyboard 

Article

# Configuring a WatchKit Scene in a Storyboard

Xcode lets you configure information about your SpriteKit Scene in your storyboard file. The following table lists the attributes you can configure in your storyboard and their meaning.

## Overview

| Attribute | Description |
|----|----|
| Scene | The SpriteKit scene to be displayed. You can also set this value programmatically using the scene property. |
| Frame Rate | The desired frame rate for the scene’s animation. You can also set this value programmatically using the preferredFramesPerSecond property. |
| Paused | A checkbox indicating whether the scene is paused. If checked, the scene’s content is fixed onscreen. No actions are executed and no physics simulation is performed. You can also configure this value programmatically using the isPaused property. |

### Enabling Full Screen Mode

By default, when a watchOS app is running, the system reserves a strip of space across the top of the screen to display the time. The app’s content is only displayed in the area below the time.

In watchOS 4 and later, SpriteKit and SceneKit scenes can fill the full screen. When full screen mode is enabled, the SpriteKit or SceneKit scene extends up, under the time. The system still displays the time in the upper-right corner with a gradient behind it, making it clearly visible against the scene.

To enable full screen mode, place a SpriteKit or SceneKit scene as the interface controller’s only content. Then, in the interface controller’s Attribute inspector, enable the Full Screen attribute.

