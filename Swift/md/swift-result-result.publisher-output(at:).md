

- Swift
- Result
- Result.Publisher
-  output(at:) 

Instance Method

# output(at:)

Publishes a specific element, indicated by its index in the sequence of published elements.

SwiftCombineiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func output(at index: Int) -> Publishers.Output
```

## Parameters 

`index`  

The index that indicates the element to publish.

## Return Value

A publisher that publishes a specific indexed element.

## Discussion

Use output(at:) when you need to republish a specific element specified by its position in the stream. If the publisher completes normally or with an error before publishing the specified element, then the publisher doesn’t produce any elements.

In the example below, the array publisher emits the fifth element in the sequence of published elements:

```
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.publisher
    .output(at: 5)
    .sink { print("\($0)") }

// Prints: "6"
```

