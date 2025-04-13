

- Swift
- Result
- Result.Publisher
-  prepend(\_:) 

Instance Method

# prepend(\_:)

Prefixes a publisher’s output with the specified values.

SwiftCombineiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func prepend(_ elements: Self.Output...) -> Publishers.Concatenate, Self>
```

## Parameters 

`elements`  

The elements to publish before this publisher’s elements.

## Return Value

A publisher that prefixes the specified elements prior to this publisher’s elements.

## Discussion

Use `Publisher/prepend(_:)-7wk5l` when you need to prepend specific elements before the output of a publisher.

In the example below, the `Publisher/prepend(_:)-7wk5l` operator publishes the provided elements before republishing all elements from `dataElements`:

```
let dataElements = (0...10)
cancellable = dataElements.publisher
    .prepend(0, 1, 255)
    .sink { print("\($0)", terminator: " ") }

// Prints: "0 1 255 0 1 2 3 4 5 6 7 8 9 10"
```

