

- SpriteKit
- SKScene
-  Scaling a Scene’s Content to Fit the View 

Article

# Scaling a Scene’s Content to Fit the View

Configure the scale mode to determine how a scene is sized to fit its view.

## Overview

Set the scene’s scaleMode property to determine how it’s sized according to the view that’s displaying it. For example, in iOS, `scaleMode` determines the automatic resizing of your scene when the device changes orientation. In macOS, `scaleMode` affects how your scene is scaled when the user changes the size or proportions of your app’s window.

### Decide Which Scale Mode Is Best

When you design your game, you should decide on a strategy for handling the scene’s `size` and scaleMode properties. Here are the most common strategies:

- Instantiate the scene with a constant size and never change it. Pick a scaling mode that lets the view scale the scene’s content. This gives the scene a predictable coordinate system and frame. You can then base your art assets and gameplay logic on this coordinate system.

- Adjust the size of the scene in your game. Where necessary, adjust your game logic and art assets to match the scene’s size.

- Set the scaleMode property to SKSceneScaleMode.resizeFill. SpriteKit automatically resizes the scene so that it always matches the view’s size. Where necessary, adjust your game logic and art assets to match the scene’s size.

### Set a Fixed Aspect Ratio

Listing 1 shows a typical implementation for when you plan to use a constant-sized scene. This code specifies a method to be executed the first time that the scene is presented. It configures the scene’s properties, including its scaling mode, then adds content. In this example, the scale mode is set to SKSceneScaleMode.aspectFit, which scales the contents equally in both dimensions and ensures that all of the scene’s contents are visible. Where necessary, this mode adds letter-boxing.

Listing 1. Creating a constant-sized scene

- Swift
- Obj-C

```
func createSceneContent() {
    scene.scaleMode = .aspectFit
    scene.backgroundColor = .black
    // Add additional scene contents here.  
   ...
}
```

```
- (void)createSceneContent  
{      
    self.scaleMode = SKSceneScaleModeAspectFit;      
    self.backgroundColor = [SKColor blackColor];  
    // Add additional scene contents here.  
    ...
}
```

### Update Your Graphics on Scene Resize

If you expect a scene’s size to change at runtime, then the initial scene size should be used to determine which art assets to use, as well as any game logic that is dependent on the scene size. Your game should also override the scene’s didChangeSize(_:) method, which is called whenever the scene changes size. When this method is called, you should update the scene’s contents to match the new size.

## See Also

### Stretching Content to Fit the View

var scaleMode: SKSceneScaleMode

A setting that defines how the scene is mapped to the view that presents it.

enum SKSceneScaleMode

The modes that determine how the scene’s area is mapped to the view that presents it.

