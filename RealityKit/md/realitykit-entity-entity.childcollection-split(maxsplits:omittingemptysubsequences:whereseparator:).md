

- RealityKit
- Entity
- Entity.ChildCollection
-  split(maxSplits:omittingEmptySubsequences:whereSeparator:) 

Instance Method

# split(maxSplits:omittingEmptySubsequences:whereSeparator:)

Returns the longest possible subsequences of the collection, in order, that don’t contain elements satisfying the given predicate.

RealityKitSwiftiOSiPadOSMac CatalystmacOSvisionOS

``` source
func split(
    maxSplits: Int = Int.max,
    omittingEmptySubsequences: Bool = true,
    whereSeparator isSeparator: (Self.Element) throws -> Bool
) rethrows -> [Self.SubSequence]
```

## Parameters 

`maxSplits`  

The maximum number of times to split the collection, or one less than the number of subsequences to return. If `maxSplits + 1` subsequences are returned, the last one is a suffix of the original collection containing the remaining elements. `maxSplits` must be greater than or equal to zero. The default value is `Int.max`.

`omittingEmptySubsequences`  

If `false`, an empty subsequence is returned in the result for each pair of consecutive elements satisfying the `isSeparator` predicate and for each element at the start or end of the collection satisfying the `isSeparator` predicate. The default value is `true`.

`isSeparator`  

A closure that takes an element as an argument and returns a Boolean value indicating whether the collection should be split at that element.

## Return Value

An array of subsequences, split from this collection’s elements.

## Discussion

The resulting array consists of at most `maxSplits + 1` subsequences. Elements that are used to split the sequence are not returned as part of any subsequence.

The following examples show the effects of the `maxSplits` and `omittingEmptySubsequences` parameters when splitting a string using a closure that matches spaces. The first use of `split` returns each word that was originally separated by one or more spaces.

```
let line = "BLANCHE:   I don't want realism. I want magic!"
print(line.split(whereSeparator: { $0 == " " }))
// Prints "["BLANCHE:", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"
```

The second example passes `1` for the `maxSplits` parameter, so the original string is split just once, into two new strings.

```
print(line.split(maxSplits: 1, whereSeparator: { $0 == " " }))
// Prints "["BLANCHE:", "  I don\'t want realism. I want magic!"]"
```

The final example passes `false` for the `omittingEmptySubsequences` parameter, so the returned array contains empty strings where spaces were repeated.

```
print(line.split(omittingEmptySubsequences: false, whereSeparator: { $0 == " " }))
// Prints "["BLANCHE:", "", "", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"
```

Complexity

O(*n*), where *n* is the length of the collection.

## See Also

### Splitting the collection

func split(separator: Self.Element, maxSplits: Int, omittingEmptySubsequences: Bool) -> [Self.SubSequence]

Returns the longest possible subsequences of the collection, in order, around elements equal to the given element.

