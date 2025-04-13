

- Swift
- CollectionDifference
-  starts(with:by:) 

Instance Method

# starts(with:by:)

Returns a Boolean value indicating whether the initial elements of the sequence are equivalent to the elements in another sequence, using the given predicate as the equivalence test.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func starts(
    with possiblePrefix: PossiblePrefix,
    by areEquivalent: (Self.Element, PossiblePrefix.Element) throws -> Bool
) rethrows -> Bool where PossiblePrefix : Sequence
```

## Parameters 

`possiblePrefix`  

A sequence to compare to this sequence.

`areEquivalent`  

A predicate that returns `true` if its two arguments are equivalent; otherwise, `false`.

## Return Value

`true` if the initial elements of the sequence are equivalent to the elements of `possiblePrefix`; otherwise, `false`. If `possiblePrefix` has no elements, the return value is `true`.

## Discussion

The predicate must be an *equivalence relation* over the elements. That is, for any elements `a`, `b`, and `c`, the following conditions must hold:

- `areEquivalent(a, a)` is always `true`. (Reflexivity)

- `areEquivalent(a, b)` implies `areEquivalent(b, a)`. (Symmetry)

- If `areEquivalent(a, b)` and `areEquivalent(b, c)` are both `true`, then `areEquivalent(a, c)` is also `true`. (Transitivity)

Complexity

O(*m*), where *m* is the lesser of the length of the sequence and the length of `possiblePrefix`.

