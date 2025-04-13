

- RealityKit
- USD Assets
- USDZ schemas for AR
-  playbackMode 

Article

# playbackMode

Metadata that controls animation idling until a behavior takes over.

## Overview

Set the `playbackMode` metadata on the document’s *stage*, that is, the outermost container for scene description. For more information about setting stage metadata, see UsdStage \> Stage Metadata.

When an asset specifies playback metadata and a start animation, the animation plays automatically and loops until a trigger executes the `StartAnimationAction`. After the start animation completes, the asset’s behaviors (Preliminary_Behavior) take control of the animation. If you don’t define a start animation for the asset, this property indicates whether an animation should restart after it finishes playing.

### Declaration

```
uniform token playbackMode = "loop" (       
    allowedTokens = ["none","loop"]
)
```

### Playback Modes

`none`  
Runs a start animation only once until the system fires an animation trigger.

`loop`  
Plays a start animation on a loop until the system fires an animation trigger.

### Specify an initial idling animation

The following metadata demonstrates `playbackMode` for an asset that defines a StartAnimationAction. This example sets playbackMode to `loop`, idling the animation in a perpetual replay until a trigger executes the start action.

```
#usda 1.0
(
    endTimeCode = 300
    startTimeCode = 1
    timeCodesPerSecond = 30
    playbackMode = "loop"
    upAxis = "Y"
)

def Xform "AnimatedModel"
{
    def Xform "body"
    {
        double3 xformOp:translate.timeSamples = { ... }
        uniform token[] xformOpOrder = ["xformOp:translate"]
        ...
    }
    ...
}
```

## See Also

### Animation

autoPlay

Metadata that specifies whether an animation plays automatically on load.

