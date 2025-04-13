

- Swift
- Slice
-  contains(where:) 

Instance Method

# contains(where:)

Returns a Boolean value indicating whether the sequence contains an element that satisfies the given predicate.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func contains(where predicate: (Self.Element) throws -> Bool) rethrows -> Bool
```

## Parameters 

`predicate`  

A closure that takes an element of the sequence as its argument and returns a Boolean value that indicates whether the passed element represents a match.

## Return Value

`true` if the sequence contains an element that satisfies `predicate`; otherwise, `false`.

## Discussion

You can use the predicate to check for an element of a type that doesn’t conform to the `Equatable` protocol, such as the `HTTPResponse` enumeration in this example.

```
enum HTTPResponse {
    case ok
    case error(Int)
}

let lastThreeResponses: [HTTPResponse] = [.ok, .ok, .error(404)]
let hadError = lastThreeResponses.contains { element in
    if case .error = element {
        return true
    } else {
        return false
    }
}
// 'hadError' == true
```

Alternatively, a predicate can be satisfied by a range of `Equatable` elements or a general condition. This example shows how you can check an array for an expense greater than \$100.

```
let expenses = [21.37, 55.21, 9.32, 10.18, 388.77, 11.41]
let hasBigPurchase = expenses.contains { $0 > 100 }
// 'hasBigPurchase' == true
```

Complexity

O(*n*), where *n* is the length of the sequence.

