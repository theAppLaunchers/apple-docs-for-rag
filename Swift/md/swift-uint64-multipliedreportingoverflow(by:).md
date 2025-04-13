

- Swift
- UInt64
-  multipliedReportingOverflow(by:) 

Instance Method

# multipliedReportingOverflow(by:)

Returns the product of this value and the given value, along with a Boolean value indicating whether overflow occurred in the operation.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func multipliedReportingOverflow(by other: UInt64) -> (partialValue: UInt64, overflow: Bool)
```

## Return Value

A tuple containing the result of the multiplication along with a Boolean value indicating whether overflow occurred. If the `overflow` component is `false`, the `partialValue` component contains the entire product. If the `overflow` component is `true`, an overflow occurred and the `partialValue` component contains the truncated product of this value and `rhs`.

