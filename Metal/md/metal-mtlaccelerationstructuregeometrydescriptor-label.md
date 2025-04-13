

- Metal
- MTLAccelerationStructureGeometryDescriptor
-  label 

Instance Property

# label

A label for the geometry structure, suitable for debugging.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 16.0+visionOS 1.0+

``` source
var label: String? { get set }
```

## See Also

### Specifying Base Geometry Properties

var intersectionFunctionTableOffset: Int

An index into the intersection table for determining which intersection function Metal calls when it intersects a ray with the acceleration structure.

var opaque: Bool

A Boolean value that determines whether the geometry data in the acceleration structure needs to skip triangle-intersection tests.

var allowDuplicateIntersectionFunctionInvocation: Bool

A Boolean value that indicates whether Metal calls the ray-intersection test more than once per primitive on the structure.

