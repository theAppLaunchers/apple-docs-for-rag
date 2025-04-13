

- UIKit
- UIBandSelectionInteraction
-  shouldBeginHandler 

Instance Property

# shouldBeginHandler

The handler that determines whether to start a band selection interaction.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+visionOS 1.0+

``` source
@MainActor
var shouldBeginHandler: ((UIBandSelectionInteraction, CGPoint) -> Bool)? { get set }
```

## Discussion

This property stores an optional handler block you use to selectively start the interaction. If you provide a handler, the UIBandSelectionInteraction object calls your handler upon successful recognition of the appropriate event sequence, but before it starts the interaction. Use your handler to specify whether you want the interaction to proceed.

Your handler block returns a Boolean that indicates whether to start the interaction. Return true to start the interaction or false to ignore the interaction and return the UIBandSelectionInteraction object to the UIBandSelectionInteraction.State.possible state. The interaction object passes the following points to your handler:

interaction  
The UIBandSelectionInteraction object that’s ready to start the interaction.

point  
The starting point of the interaction, in your view’s coordinate space. You might use this value to prevent someone from starting interactions in disabled items or from specific regions of your view.

