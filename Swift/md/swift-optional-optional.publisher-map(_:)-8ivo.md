

- Swift
- Optional
- Optional.Publisher
-  map(\_:) 

Instance Method

# map(\_:)

Transforms all elements from the upstream publisher with a provided closure.

SwiftCombineiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func map(_ transform: @escaping (Self.Output) -> T) -> Publishers.Map
```

## Parameters 

`transform`  

A closure that takes one element as its parameter and returns a new element.

## Return Value

A publisher that uses the provided closure to map elements from the upstream publisher to new elements that it then publishes.

## Discussion

Combine’s `Publisher/map(_:)-99evh` operator performs a function similar to that of map(_:) in the Swift standard library: it uses a closure to transform each element it receives from the upstream publisher. You use `Publisher/map(_:)-99evh` to transform from one kind of element to another.

The following example uses an array of numbers as the source for a collection based publisher. A `Publisher/map(_:)-99evh` operator consumes each integer from the publisher and uses a dictionary to transform it from its Arabic numeral to a Roman equivalent, as a String. If the `Publisher/map(_:)-99evh`’s closure fails to look up a Roman numeral, it returns the string `(unknown)`.

```
let numbers = [5, 4, 3, 2, 1, 0]
let romanNumeralDict: [Int : String] =
   [1:"I", 2:"II", 3:"III", 4:"IV", 5:"V"]
cancellable = numbers.publisher
    .map { romanNumeralDict[$0] ?? "(unknown)" }
    .sink { print("\($0)", terminator: " ") }

// Prints: "V IV III II I (unknown)"
```

If your closure can throw an error, use Combine’s tryMap(_:) operator instead.

