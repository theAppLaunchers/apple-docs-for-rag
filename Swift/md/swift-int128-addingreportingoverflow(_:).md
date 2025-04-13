

- Swift
- Int128
-  addingReportingOverflow(\_:) 

Instance Method

# addingReportingOverflow(\_:)

Returns the sum of this value and the given value, along with a Boolean value indicating whether overflow occurred in the operation.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
func addingReportingOverflow(_ other: Int128) -> (partialValue: Int128, overflow: Bool)
```

## Return Value

A tuple containing the result of the addition along with a Boolean value indicating whether overflow occurred. If the `overflow` component is `false`, the `partialValue` component contains the entire sum. If the `overflow` component is `true`, an overflow occurred and the `partialValue` component contains the truncated sum of this value and `rhs`.

