

- Synchronization
- Atomic
-  compareExchange(expected:desired:successOrdering:failureOrdering:) 

Instance Method

# compareExchange(expected:desired:successOrdering:failureOrdering:)

Perform an atomic compare and exchange operation on the current value, applying the specified success/failure memory orderings.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
func compareExchange(
    expected: consuming Value,
    desired: consuming Value,
    successOrdering: AtomicUpdateOrdering,
    failureOrdering: AtomicLoadOrdering
) -> (exchanged: Bool, original: Value)
```

Available when `Value` conforms to `AtomicRepresentable` and `Value.AtomicRepresentation` is `_Atomic128BitStorage`.

## Parameters 

`expected`  

The expected current value.

`desired`  

The desired new value.

`successOrdering`  

The memory ordering to apply if this operation performs the exchange.

`failureOrdering`  

The memory ordering to apply on this operation does not perform the exchange.

## Return Value

A tuple `(exchanged, original)`, where `exchanged` is true if the exchange was successful, and `original` is the original value.

## Discussion

This operation performs the following algorithm as a single atomic transaction:

```
atomic(self) { currentValue in
  let original = currentValue
  guard original == expected else { return (false, original) }
  currentValue = desired
  return (true, original)
}
```

The `successOrdering` argument specifies the memory ordering to use when the operation manages to update the current value, while `failureOrdering` will be used when the operation leaves the value intact.

Note

This method implements a “strong” compare and exchange operation that does not permit spurious failures.

