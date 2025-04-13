

- Swift
- Int
-  remainderReportingOverflow(dividingBy:) 

Instance Method

# remainderReportingOverflow(dividingBy:)

Returns the remainder after dividing this value by the given value, along with a Boolean value indicating whether overflow occurred during division.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func remainderReportingOverflow(dividingBy other: Int) -> (partialValue: Int, overflow: Bool)
```

## Return Value

A tuple containing the result of the operation along with a Boolean value indicating whether overflow occurred. If the `overflow` component is `false`, the `partialValue` component contains the entire remainder. If the `overflow` component is `true`, an overflow occurred during division and the `partialValue` component contains either the entire remainder or, if the remainder is undefined, the dividend.

## Discussion

Dividing by zero is not an error when using this method. For a value `x`, the result of `x.remainderReportingOverflow(dividingBy: 0)` is `(x, true)`.

## See Also

### Performing Calculations with Overflow

func addingReportingOverflow(Int) -> (partialValue: Int, overflow: Bool)

Returns the sum of this value and the given value, along with a Boolean value indicating whether overflow occurred in the operation.

func subtractingReportingOverflow(Int) -> (partialValue: Int, overflow: Bool)

Returns the difference obtained by subtracting the given value from this value, along with a Boolean value indicating whether overflow occurred in the operation.

func multipliedReportingOverflow(by: Int) -> (partialValue: Int, overflow: Bool)

Returns the product of this value and the given value, along with a Boolean value indicating whether overflow occurred in the operation.

func dividedReportingOverflow(by: Int) -> (partialValue: Int, overflow: Bool)

Returns the quotient obtained by dividing this value by the given value, along with a Boolean value indicating whether overflow occurred in the operation.

