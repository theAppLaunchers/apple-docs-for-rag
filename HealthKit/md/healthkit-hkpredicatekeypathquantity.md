

- HealthKit
-  HKPredicateKeyPathQuantity 

Global Variable

# HKPredicateKeyPathQuantity

The key path for accessing the sample’s quantity.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 13.0+visionOS 1.0+watchOS 2.0+

``` source
let HKPredicateKeyPathQuantity: String
```

## Discussion

Use this constant whenever you want to include a sample’s quantity in a predicate format string. Add a `%K` placeholder to the format string, and then pass this constant as an argument.

Alternatively, use the predicateForQuantitySamples(with:quantity:) method to create predicates that match a sample’s quantity.

## See Also

### Specifying Predicate Key Paths

let HKPredicateKeyPathCount: String

A key path for the sample’s count.

