

- AppKit
- NSTextRange
-  intersection(\_:) 

Instance Method

# intersection(\_:)

Returns the range, if any, where two text ranges intersect.

macOS 12.0+

``` source
func intersection(_ textRange: NSTextRange) -> Self?
```

## Parameters 

`textRange`  

The range used to compare against the current range to evaluate for differences.

## Return Value

An NSRange that represents the intersection of the ranges, or `nil` if they don’t intersect.

## See Also

### Comparing text ranges

func intersects(NSTextRange) -> Bool

Determines if two ranges intersect.

func isEqual(to: NSTextRange) -> Bool

Compares two text ranges.

func union(NSTextRange) -> Self

Returns a new text range by forming the union with the text range you provide.

