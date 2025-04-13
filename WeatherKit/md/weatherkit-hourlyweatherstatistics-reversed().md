

- WeatherKit
- HourlyWeatherStatistics
-  reversed() 

Instance Method

# reversed()

Returns a view presenting the elements of the collection in reverse order.

WeatherKitSwiftiOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
func reversed() -> ReversedCollection
```

## Discussion

You can reverse a collection without allocating new space for its elements by calling this `reversed()` method. A `ReversedCollection` instance wraps an underlying collection and provides access to its elements in reverse order. This example prints the characters of a string in reverse order:

```
let word = "Backwards"
for char in word.reversed() {
    print(char, terminator: "")
}
// Prints "sdrawkcaB"
```

If you need a reversed collection of the same type, you may be able to use the collection’s sequence-based or collection-based initializer. For example, to get the reversed version of a string, reverse its characters and initialize a new `String` instance from the result.

```
let reversedWord = String(word.reversed())
print(reversedWord)
// Prints "sdrawkcaB"
```

Complexity

O(1)

