

- Swift
- Hasher
-  finalize() 

Instance Method

# finalize()

Finalizes the hasher state and returns the hash value.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func finalize() -> Int
```

## Return Value

The hash value calculated by the hasher.

## Discussion

Finalizing consumes the hasher: it is illegal to finalize a hasher you don’t own, or to perform operations on a finalized hasher. (These may become compile-time errors in the future.)

Hash values are not guaranteed to be equal across different executions of your program. Do not save hash values to use during a future execution.

