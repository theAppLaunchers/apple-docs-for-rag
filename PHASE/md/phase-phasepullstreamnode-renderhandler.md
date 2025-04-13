

- PHASE
- PHASEPullStreamNode
-  renderHandler 

Instance Property

# renderHandler

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
var renderHandler: PHASEPullStreamRenderHandler { get set }
```

## Discussion

```
@property renderBlock
@abstract A property to set the render block callback that will render the samplesIW
@discussion
    The renderBlock must be set before the PHASESoundEvent is prepared or started.  The callback will be called from a high priority realtime thread.
    Your implementation must be performant and not perform any realtime unsafe operations such as lock mutexes or allocate memory.
```

