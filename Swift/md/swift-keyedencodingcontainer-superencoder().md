

- Swift
- KeyedEncodingContainer
-  superEncoder() 

Instance Method

# superEncoder()

Stores a new nested container for the default `super` key and returns a new encoder instance for encoding `super` into that container.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
mutating func superEncoder() -> any Encoder
```

## Return Value

A new encoder to pass to `super.encode(to:)`.

## Discussion

Equivalent to calling `superEncoder(forKey:)` with `Key(stringValue: "super", intValue: 0)`.

