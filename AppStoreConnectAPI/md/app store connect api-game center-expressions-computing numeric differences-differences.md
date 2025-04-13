

- App Store Connect API
- Game Center
- Expressions
-  Computing numeric differences 

Article

# Computing numeric differences

Return the absolute difference between the maximum and minimum numerical values in an array.

## Overview

Use the `diff()` function in the expression of a matchmaking rule to compute the greatest difference between two or more values. For example, `diff([ `4`, `3`, `2`, `1` ])` returns `3`, and `diff([ `50`, `19`, `21`, `61` ]` returns `42`.

### Declaration

```
number diff(array[number] $values)
```

### Parameters

`values`  
An array that contains the numeric values to compare.

### Return value

The absolute difference between the maximum and minimum items in the `values` array.

## See Also

### Array functions

Converting arrays to sets

Return the content of a list, with duplicates removed and sorted, so that you can compare it to another set.

Intersecting sets

Return the intersection of two or more arrays treated as sets.

