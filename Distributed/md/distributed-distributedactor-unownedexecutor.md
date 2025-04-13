

- Distributed
- DistributedActor
-  unownedExecutor 

Instance Property

# unownedExecutor

Retrieve the executor for this distributed actor as an optimized, unowned reference. This API is equivalent to `Actor/unownedExecutor`, however, by default, it intentionally returns `nil` if this actor is a reference to a remote distributed actor, because the executor for remote references is effectively never g

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOSwatchOS 10.0+

``` source
nonisolated
var unownedExecutor: UnownedSerialExecutor { get }
```

**Required**

## Custom implementation requirements

This property must always evaluate to the same executor for a given actor instance, and holding on to the actor must keep the executor alive.

This property will be implicitly accessed when work needs to be scheduled onto this actor. These accesses may be merged, eliminated, and rearranged with other work, and they may even be introduced when not strictly required. Visible side effects are therefore strongly discouraged within this property.

