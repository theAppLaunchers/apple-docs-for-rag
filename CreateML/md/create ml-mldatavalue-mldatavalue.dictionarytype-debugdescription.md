

- Create ML
- MLDataValue
- MLDataValue.DictionaryType
-  debugDescription 

Instance Property

# debugDescription

A textual representation of this instance, suitable for debugging.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 10.14+tvOS 16.0+visionOS 1.0+

``` source
var debugDescription: String { get }
```

## Discussion

Calling this property directly is discouraged. Instead, convert an instance of any type to a string by using the `String(reflecting:)` initializer. This initializer works with any type, and uses the custom `debugDescription` property for types that conform to `CustomDebugStringConvertible`:

```
struct Point: CustomDebugStringConvertible {
    let x: Int, y: Int

    var debugDescription: String {
        return "(\(x), \(y))"
    }
}

let p = Point(x: 21, y: 30)
let s = String(reflecting: p)
print(s)
// Prints "(21, 30)"
```

The conversion of `p` to a string in the assignment to `s` uses the `Point` type’s `debugDescription` property.

