

- Swift
- JoinedSequence
-  split(maxSplits:omittingEmptySubsequences:whereSeparator:) 

Instance Method

# split(maxSplits:omittingEmptySubsequences:whereSeparator:)

Returns the longest possible subsequences of the sequence, in order, that don’t contain elements satisfying the given predicate. Elements that are used to split the sequence are not returned as part of any subsequence.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func split(
    maxSplits: Int = Int.max,
    omittingEmptySubsequences: Bool = true,
    whereSeparator isSeparator: (Self.Element) throws -> Bool
) rethrows -> [ArraySlice]
```

## Parameters 

`maxSplits`  

The maximum number of times to split the sequence, or one less than the number of subsequences to return. If `maxSplits + 1` subsequences are returned, the last one is a suffix of the original sequence containing the remaining elements. `maxSplits` must be greater than or equal to zero. The default value is `Int.max`.

`omittingEmptySubsequences`  

If `false`, an empty subsequence is returned in the result for each pair of consecutive elements satisfying the `isSeparator` predicate and for each element at the start or end of the sequence satisfying the `isSeparator` predicate. If `true`, only nonempty subsequences are returned. The default value is `true`.

`isSeparator`  

A closure that returns `true` if its argument should be used to split the sequence; otherwise, `false`.

## Return Value

An array of subsequences, split from this sequence’s elements.

## Discussion

The following examples show the effects of the `maxSplits` and `omittingEmptySubsequences` parameters when splitting a string using a closure that matches spaces. The first use of `split` returns each word that was originally separated by one or more spaces.

```
let line = "BLANCHE:   I don't want realism. I want magic!"
print(line.split(whereSeparator: { $0 == " " })
          .map(String.init))
// Prints "["BLANCHE:", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"
```

The second example passes `1` for the `maxSplits` parameter, so the original string is split just once, into two new strings.

```
print(
   line.split(maxSplits: 1, whereSeparator: { $0 == " " })
                  .map(String.init))
// Prints "["BLANCHE:", "  I don\'t want realism. I want magic!"]"
```

The final example passes `true` for the `allowEmptySlices` parameter, so the returned array contains empty strings where spaces were repeated.

```
print(
    line.split(
        omittingEmptySubsequences: false,
        whereSeparator: { $0 == " " }
    ).map(String.init))
// Prints "["BLANCHE:", "", "", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"
```

Complexity

O(*n*), where *n* is the length of the sequence.

