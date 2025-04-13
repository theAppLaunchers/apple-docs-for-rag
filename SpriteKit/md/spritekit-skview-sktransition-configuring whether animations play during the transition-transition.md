

- SpriteKit
- SKView
- SKTransition
-  Configuring Whether Animations Play During the Transition 

Article

# Configuring Whether Animations Play During the Transition

## Overview

The pausesIncomingScene and pausesOutgoingScene properties on the transition object define which animations are played during the transition. By default, both scenes are paused during the transition. However, you might want to enable animation on either scene during the transition.

Figure 1 illustrates which frames of the incoming and outgoing scenes are displayed on screen during a three frame transition with different permutations of pausesIncomingScene and pausesOutgoingScene.

For example, consider the code again in . Because the button is going to run an action, this code expects the outgoing scene to be animated. But perhaps the incoming scene should not animate its content until the transition completes. Adding the code in Listing 1 has the desired effect.

Listing 1. Pausing frame processing during a transition

- Swift
- Obj-C

```
reveal.pausesOutgoingScene = true;
reveal.pausesIncomingScene = false;
```

```
reveal.pausesOutgoingScene = YES;
reveal.pausesIncomingScene = NO;
```

## See Also

### Creating Transitions

Transitioning Between Two Scenes

class func crossFade(withDuration: TimeInterval) -> SKTransition

Creates a cross fade transition.

class func doorsCloseHorizontal(withDuration: TimeInterval) -> SKTransition

Creates a transition where the new scene appears as a pair of closing horizontal doors.

class func doorsCloseVertical(withDuration: TimeInterval) -> SKTransition

Creates a transition where the new scene appears as a pair of closing vertical doors.

class func doorsOpenHorizontal(withDuration: TimeInterval) -> SKTransition

Creates a transition where the new scene appears as a pair of opening horizontal doors.

class func doorsOpenVertical(withDuration: TimeInterval) -> SKTransition

Creates a transition where the new scene appears as a pair of opening vertical doors.

class func doorway(withDuration: TimeInterval) -> SKTransition

Creates a transition where the previous scene disappears as a pair of opening doors.

class func fade(with: UIColor, duration: TimeInterval) -> SKTransition

Creates a transition that first fades to a constant color and then fades to the new scene.

class func fade(withDuration: TimeInterval) -> SKTransition

Creates a transition that first fades to black and then fades to the new scene.

class func flipHorizontal(withDuration: TimeInterval) -> SKTransition

Creates a transition where the two scenes are flipped across a horizontal line running through the center of the view.

class func flipVertical(withDuration: TimeInterval) -> SKTransition

Creates a transition where the two scenes are flipped across a vertical line running through the center of the view.

class func moveIn(with: SKTransitionDirection, duration: TimeInterval) -> SKTransition

Creates a transition where the new scene moves in on top of the old scene.

class func push(with: SKTransitionDirection, duration: TimeInterval) -> SKTransition

Creates a transition where the new scene moves in, pushing the old scene out of the view.

class func reveal(with: SKTransitionDirection, duration: TimeInterval) -> SKTransition

Creates a transition where the old scene moves out of the view, revealing the new scene underneath it.

init(ciFilter: CIFilter, duration: TimeInterval)

Creates a transition that uses a Core Image filter to perform the transition.

