

- SpriteKit
- SKScene
- SKSceneDelegate
-  Use SpriteKit Objects within Scene Delegate Callbacks 

Article

# Use SpriteKit Objects within Scene Delegate Callbacks

Follow threading guidelines to keep your SpriteKit app thread safe.

## Overview

SpriteKit is largely a single threaded game engine and as such the API provides developers with callbacks to implement your custom game logic. The primary callback for your game logic is update(_:for:). Other callbacks are illustrated in SKSceneDelegate. Modifying SpriteKit objects outside of the scene delegate callbacks (such as in a background queue or anything else not running on the main thread) can result in concurrency related problems. Even dispatching work on the main thread asynchronously or at a later time is risky because the closure is likely to be done outside of the timeframe SpriteKit expects. If you’re experiencing a segmentation fault or other type of crash occurring deep within the SpriteKit framework, there’s a good chance your code is modifying a SpriteKit object outside of the scene delegate callbacks.

Note

To check at runtime if a particular block of code is running on the main thread, inspect isMainThread.

## See Also

### Handling Animation Events

func update(TimeInterval, for: SKScene)

Tells you to perform any app specific logic to update your scene.

func didEvaluateActions(for: SKScene)

Tells you to peform any necessary logic after scene actions are evaluated.

func didSimulatePhysics(for: SKScene)

Tells you to peform any necessary logic after physics simulations are performed.

func didApplyConstraints(for: SKScene)

Tells you to peform any necessary logic after constraints are applied.

func didFinishUpdate(for: SKScene)

Tells you to peform any necessary logic after the scene has finished all of the steps required to process animations.

