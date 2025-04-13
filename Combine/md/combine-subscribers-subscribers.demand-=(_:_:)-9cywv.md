

- Combine
- Subscribers
- Subscribers.Demand
-  \

Operator

# \

Returns a Boolean value that indicates whether the first demand requests fewer or the same number of elements as the second.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
static func  Bool
```

## Discussion

If both sides are `.unlimited`, the result is always `true`. If `lhs` is `.unlimited`, then the result is always `false`. If `rhs` is unlimited then the result is always `true`. Otherwise, this operator compares the demands’ `max` values.

