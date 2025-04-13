

- Core Animation
- CAAnimation
-  animationEvents 

Instance Property

# animationEvents

For animations attached to SceneKit objects, a list of events attached to an animation.

iOSiPadOSMac Catalyst 13.1+macOS 10.9+tvOSvisionOS

``` source
var animationEvents: [SCNAnimationEvent]? { get set }
```

## Discussion

An array of SCNAnimationEvent objects, each of which adds a timed action to the animation.

For example, you can create animation events that play sound effects timed to match the footsteps of an animated game character or that add new nodes to the scene when an animation completes.

To attach animations to SceneKit objects, see SCNAnimatable.

