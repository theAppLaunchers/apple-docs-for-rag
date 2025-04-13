

- RealityKit
- PhysicsBodyParameterTypes
-  PhysicsBodyParameterTypes.RawValue 

Type Alias

# PhysicsBodyParameterTypes.RawValue

The raw type that can be used to represent all values of the conforming type.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
typealias RawValue = UInt32
```

## Discussion

Every distinct value of the conforming type has a corresponding unique value of the `RawValue` type, but there may be values of the `RawValue` type that don’t have a corresponding value of the conforming type.

