

- Swift
- KeyValuePairs
-  last 

Instance Property

# last

The last element of the collection.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var last: Self.Element? { get }
```

## Discussion

If the collection is empty, the value of this property is `nil`.

```
let numbers = [10, 20, 30, 40, 50]
if let lastNumber = numbers.last {
    print(lastNumber)
}
// Prints "50"
```

Complexity

O(1)

