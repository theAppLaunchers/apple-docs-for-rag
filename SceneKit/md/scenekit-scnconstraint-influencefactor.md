

- SceneKit
- SCNConstraint
-  influenceFactor 

Instance Property

# influenceFactor

The influence of the constraint on the node’s transformation.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
var influenceFactor: CGFloat { get set }
```

## Discussion

Use this property to relax the effect of a constraint on the nodes it applies to. For example, consider a node containing a spotlight, constrained by an SCNLookAtConstraint object to point toward another node containing a moving game character. If the constraint’s influence factor is `1.0`, SceneKit adjusts the spotlight node to point directly at the game character each time it renders a frame. If you reduce the influence factor to `0.5`, each time SceneKit renders a frame it moves the spotlight halfway from its current orientation to the target orientation. As a result, the spotlight continues to follow the moving character, but with a slight lag.

The default influence factor is `1.0`, specifying that SceneKit apply the full effect of the constraint every frame. An influence factor of `0.0` means the constraint has no effect.

This property has no effect on SCNTransformConstraint objects.

