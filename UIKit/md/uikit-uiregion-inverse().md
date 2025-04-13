

- UIKit
- UIRegion
-  inverse() 

Instance Method

# inverse()

Returns a new region that’s the mathematical inverse of the current region.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
func inverse() -> Self
```

## Return Value

A new region whose contents include all points that are not in the current region.

## Discussion

The inverse of the infinite region is an empty region.

## See Also

### Creating complex regions

func byDifference(from: UIRegion) -> Self

Returns a new region created by subtracting the specified region from the current region.

func byIntersection(with: UIRegion) -> Self

Returns a new region containing only the area occupied by both the specified region and current region.

func byUnion(with: UIRegion) -> Self

Returns a new region containing the combined areas of the specified region and the current region.

