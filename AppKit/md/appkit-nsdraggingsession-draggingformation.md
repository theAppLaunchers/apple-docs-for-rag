

- AppKit
- NSDraggingSession
-  draggingFormation 

Instance Property

# draggingFormation

Controls the dragging formation when the drag is not over the source or a valid destination.

macOS 10.7+

``` source
var draggingFormation: NSDraggingFormation { get set }
```

## Discussion

Setting this value causes the dragging formation to change immediately, provided a valid destination has not overriden the behavior. If the dragging session hasn’t started yet, the dragging items will animate into formation immediately upon start. It is *highly* recommended to never change the formation when starting a drag.

The default value is NSDraggingFormation.none.

## See Also

### Dragging Visual Representation

var animatesToStartingPositionsOnCancelOrFail: Bool

Controls whether the dragging image animates back to its starting point on a cancelled or failed drag.

