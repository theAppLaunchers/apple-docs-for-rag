

- Swift
-  ExpressibleByDictionaryLiteral 

Protocol

# ExpressibleByDictionaryLiteral

A type that can be initialized using a dictionary literal.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
protocol ExpressibleByDictionaryLiteral
```

## Overview

A dictionary literal is a simple way of writing a list of key-value pairs. You write each key-value pair with a colon (`:`) separating the key and the value. The dictionary literal is made up of one or more key-value pairs, separated by commas and surrounded with square brackets.

To declare a dictionary, assign a dictionary literal to a variable or constant:

```
let countryCodes = ["BR": "Brazil", "GH": "Ghana",
                    "JP": "Japan", "US": "United States"]
// 'countryCodes' has type '[String: String]'

print(countryCodes["BR"]!)
// Prints "Brazil"
```

When the context provides enough type information, you can use a special form of the dictionary literal, square brackets surrounding a single colon, to initialize an empty dictionary.

```
var frequencies: [String: Int] = [:]
print(frequencies.count)
// Prints "0"
```

Note

A dictionary literal is *not* the same as an instance of `Dictionary`. You can’t initialize a type that conforms to `ExpressibleByDictionaryLiteral` simply by assigning an instance of `Dictionary`, `KeyValuePairs`, or similar.

# Conforming to the ExpressibleByDictionaryLiteral Protocol

To add the capability to be initialized with a dictionary literal to your own custom types, declare an `init(dictionaryLiteral:)` initializer. The following example shows the dictionary literal initializer for a hypothetical `CountedSet` type, which uses setlike semantics while keeping track of the count for duplicate elements:

```
struct CountedSet: Collection, SetAlgebra {
    // implementation details

    /// Updates the count stored in the set for the given element,
    /// adding the element if necessary.
    ///
    /// - Parameter n: The new count for `element`. `n` must be greater
    ///   than or equal to zero.
    /// - Parameter element: The element to set the new count on.
    mutating func updateCount(_ n: Int, for element: Element)
}

extension CountedSet: ExpressibleByDictionaryLiteral {
    init(dictionaryLiteral elements: (Element, Int)...) {
        self.init()
        for (element, count) in elements {
            self.updateCount(count, for: element)
        }
    }
}
```

## Topics

### Associated Types

associatedtype Key

The key type of a dictionary literal.

**Required**

associatedtype Value

The value type of a dictionary literal.

**Required**

### Initializers

init(dictionaryLiteral: (Self.Key, Self.Value)...)

Creates an instance initialized with the given key-value pairs.

**Required**

## Relationships

### Conforming Types

- Dictionary

  Conforms when `Key` conforms to `Hashable`, `Value` conforms to `Copyable`, and `Value` conforms to `Escapable`.

- KeyValuePairs

## See Also

### Collection Literals

protocol ExpressibleByArrayLiteral

A type that can be initialized using an array literal.

