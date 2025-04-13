

- Synchronization
- Atomic
-  weakCompareExchange(expected:desired:ordering:) 

Instance Method

# weakCompareExchange(expected:desired:ordering:)

Perform an atomic weak compare and exchange operation on the current value, applying the memory ordering. This compare-exchange variant is allowed to spuriously fail; it is designed to be called in a loop until it indicates a successful exchange has happened.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
func weakCompareExchange(
    expected: consuming Value,
    desired: consuming Value,
    ordering: AtomicUpdateOrdering
) -> (exchanged: Bool, original: Value)
```

Available when `Value` conforms to `AtomicRepresentable` and `Value.AtomicRepresentation` is `_Atomic128BitStorage`.

## Parameters 

`expected`  

The expected current value.

`desired`  

The desired new value.

`ordering`  

The memory ordering to apply on this operation.

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

Note

The weakCompareExchange form may sometimes return false even when the original and expected values are equal. (Such failures may happen when some transient condition prevents the underlying operation from succeeding – such as an incoming interrupt during a load-link/store-conditional instruction sequence.) This variant is designed to be called in a loop that only exits when the exchange is successful; in such loops, using weakCompareExchange may lead to a performance improvement by eliminating a nested loop in the regular, “strong”, compareExchange variants.

