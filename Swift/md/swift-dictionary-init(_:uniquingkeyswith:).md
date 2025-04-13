

- Swift
- Dictionary
-  init(\_:uniquingKeysWith:) 

Initializer

# init(\_:uniquingKeysWith:)

Creates a new dictionary from the key-value pairs in the given sequence, using a combining closure to determine the value for any duplicate keys.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init(
    _ keysAndValues: S,
    uniquingKeysWith combine: (Value, Value) throws -> Value
) rethrows where S : Sequence, S.Element == (Key, Value)
```

## Parameters 

`keysAndValues`  

A sequence of key-value pairs to use for the new dictionary.

`combine`  

A closure that is called with the values for any duplicate keys that are encountered. The closure returns the desired value for the final dictionary.

## Discussion

You use this initializer to create a dictionary when you have a sequence of key-value tuples that might have duplicate keys. As the dictionary is built, the initializer calls the `combine` closure with the current and new values for any duplicate keys. Pass a closure as `combine` that returns the value to use in the resulting dictionary: The closure can choose between the two values, combine them to produce a new value, or even throw an error.

The following example shows how to choose the first and last values for any duplicate keys:

```
let pairsWithDuplicateKeys = [("a", 1), ("b", 2), ("a", 3), ("b", 4)]

let firstValues = Dictionary(pairsWithDuplicateKeys,
                             uniquingKeysWith: { (first, _) in first })
// ["b": 2, "a": 1]

let lastValues = Dictionary(pairsWithDuplicateKeys,
                            uniquingKeysWith: { (_, last) in last })
// ["b": 4, "a": 3]
```

## See Also

### Creating a Dictionary

init()

Creates an empty dictionary.

init(minimumCapacity: Int)

Creates an empty dictionary with preallocated space for at least the specified number of elements.

init&lt;S>(uniqueKeysWithValues: S)

Creates a new dictionary from the key-value pairs in the given sequence.

init&lt;S>(grouping: S, by: (S.Element) throws -> Key) rethrows

Creates a new dictionary whose keys are the groupings returned by the given closure and whose values are arrays of the elements that returned each key.

