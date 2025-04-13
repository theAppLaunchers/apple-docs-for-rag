

- Distributed
- DistributedActorSystem
-  assignID(\_:) 

Instance Method

# assignID(\_:)

Assign an ActorID for the passed actor type.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOSwatchOS 9.0+

``` source
func assignID(_ actorType: Act.Type) -> Self.ActorID where Act : DistributedActor, Self.ActorID == Act.ID
```

**Required**

## Discussion

This function is invoked by a distributed actor during its initialization, and the returned address value is stored along with it for the time of its lifetime.

The address MUST uniquely identify the actor, and allow resolving it. E.g. if an actor is created under address `addr1` then immediately invoking `system.resolve(id: addr1, as: Greeter.self)` MUST return a reference to the same actor.

