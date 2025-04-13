

- Matter
- MTRClusterPowerTopology
-  init(device:endpointID:queue:) 

Initializer

# init(device:endpointID:queue:)

The queue is currently unused, but may be used in the future for calling completions for command invocations if commands are added to this cluster.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+tvOS 18.4+visionOS 2.4+watchOS 11.4+

``` source
init?(
    device: MTRDevice,
    endpointID: NSNumber,
    queue: dispatch_queue_t
)
```

