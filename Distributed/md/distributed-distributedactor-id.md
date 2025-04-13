

- Distributed
- DistributedActor
-  id 

Instance Property

# id

Logical identity of this distributed actor.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOSwatchOS 9.0+

``` source
override nonisolated
var id: Self.ID { get }
```

**Required**

## Discussion

Many distributed actor references may be pointing at, logically, the same actor. For example, calling `resolve(id:using:)` multiple times, is not guaranteed to return the same exact resolved actor instance, however all the references would represent logically references to the same distributed actor, e.g. on a different node.

Depending on the capabilities of the actor system producing the identifiers, the `ID` may also be used to store instance specific metadata.

## Synthesized property

In concrete distributed actor declarations, a witness for this protocol requirement is synthesized by the compiler.

It is not possible to assign a value to the `id` directly; instead, it is assigned during an actors `init` (or `resolve`), by the managing actor system.

