

- Swift
- Result
- Result.Publisher
-  prefix(\_:) 

Instance Method

# prefix(\_:)

Republishes elements up to the specified maximum count.

SwiftCombineiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func prefix(_ maxLength: Int) -> Publishers.Output
```

## Parameters 

`maxLength`  

The maximum number of elements to republish.

## Return Value

A publisher that publishes up to the specified number of elements.

## Discussion

Use prefix(_:) to limit the number of elements republished to the downstream subscriber.

In the example below, the prefix(_:) operator limits its output to the first two elements before finishing normally:

```
let numbers = (0...10)
cancellable = numbers.publisher
    .prefix(2)
    .sink { print("\($0)", terminator: " ") }

// Prints: "0 1"
```

