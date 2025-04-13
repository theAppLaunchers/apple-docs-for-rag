

- SpriteKit
- Nodes for Scene Building
- SKEmitterNode
-  Changing the Location of Particles in Your Scene 

Article

# Changing the Location of Particles in Your Scene

Set a target node from which SpriteKit creates particles.

## Overview

When the emitter creates particles, the particles are rendered as children of the emitter node. This means that they inherit the characteristics of the emitter node, just like nodes do. For example, if you rotate the emitter node, the positions of all of the generated particles are also rotated. Depending on what effect you are simulating with the emitter, this may not be the correct behavior.

For example, assume that you are using the emitter node to create the exhaust from a rocket. When the engines are at full burn, a cone of flame should come out the back of the ship. This is easily simulated using particles. But if the particles are rendered relative to the ship, when the ship turns, the exhaust also turns, which doesn’t look right. The particles should be generated, but should thereafter be independent of the emitter node. When the emitter node is rotated, new particles get the new orientation, and old particles maintain their old orientation. You make particles independent of the emitter by specifying a target node.

The following code shows how to configure a rocket exhaust effect to use a target node. When the custom sprite node class instantiates the exhaust node, it makes the node its child. However, it redirects the particles to the scene.

- Swift
- Obj-C

```
func newExhaustNode(scene: SKScene) {
    guard let emitter = SKEmitterNode(fileNamed: "exhaust.sks") else {
        return
    }

    // Place the emitter at the rear of the ship.
    emitter.position = CGPoint(x: 0, y: -40)
    emitter.name = "exhaust"

    // Send the particles to the scene.
    emitter.targetNode = scene;
    scene.addChild(emitter)
}
```

```
- (void) newExhaustNode
{
    SKEmitterNode *emitter =  [NSKeyedUnarchiver unarchiveObjectWithFile:[[NSBundle mainBundle] pathForResource:@"exhaust" ofType:@"sks"]];

// Place the emitter at the rear of the ship.
   emitter.position = CGPointMake(0,-40);
   emitter.name = @"exhaust";
// Send the particles to the scene.
   emitter.targetNode = self.scene;

   [self addChild:emitter];
}
```

When an emitter has a target node, it calculates the position, velocity, and orientation of the particle, exactly as if it were a child of the sprite node. This means that if the ship sprite is rotated, the exhaust orientation is automatically rotated, too. However, at the moment a new particle’s starting values are calculated, the values are transformed into the target node’s coordinate system. Thereafter, they would only be affected by changes to the target node.

## See Also

### Choosing Which Node in the Scene Emits Particles

var targetNode: SKNode?

The target node that renders the emitter’s particles.

