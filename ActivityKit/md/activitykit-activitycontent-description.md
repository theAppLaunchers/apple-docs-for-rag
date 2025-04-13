

- ActivityKit
- ActivityContent
-  description 

Instance Property

# description

A textual representation of this instance.

iOS 16.2+iPadOS 16.2+

``` source
var description: String { get }
```

Available when `State` conforms to `Decodable`, `Encodable`, and `Hashable`.

## Discussion

Calling this property directly is discouraged. Instead, convert an instance of any type to a string by using the `String(describing:)` initializer. This initializer works with any type, and uses the custom `description` property for types that conform to `CustomStringConvertible`:

```
struct Point: CustomStringConvertible {
    let x: Int, y: Int

    var description: String {
        return "(\(x), \(y))"
    }
}

let p = Point(x: 21, y: 30)
let s = String(describing: p)
print(s)
// Prints "(21, 30)"
```

The conversion of `p` to a string in the assignment to `s` uses the `Point` type’s `description` property.

