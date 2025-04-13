

- Observation
- ObservationRegistrar
-  hash(into:) 

Instance Method

# hash(into:)

Hashes the essential components of this value by feeding them into the given hasher.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
func hash(into hasher: inout Hasher)
```

## Parameters 

`hasher`  

The hasher to use when combining the components of this instance.

## Discussion

Implement this method to conform to the `Hashable` protocol. The components used for hashing must be the same as the components compared in your type’s `==` operator implementation. Call `hasher.combine(_:)` with each of these components.

Important

In your implementation of `hash(into:)`, don’t call `finalize()` on the `hasher` instance provided, or replace it with a different instance. Doing so may become a compile-time error in the future.

