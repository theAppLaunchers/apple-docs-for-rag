

- TabularData
- AnyColumn
-  distinct() 

Instance Method

# distinct()

Generates a column slice that contains unique elements.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
func distinct() -> AnyColumnSlice
```

## Return Value

A type-erased column slice.

## Discussion

The method only adds the first of multiple elements with the same value — the element with the smallest index — to the slice.

