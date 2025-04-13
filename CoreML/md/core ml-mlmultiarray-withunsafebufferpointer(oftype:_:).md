

- Core ML
- MLMultiArray
-  withUnsafeBufferPointer(ofType:\_:) 

Instance Method

# withUnsafeBufferPointer(ofType:\_:)

Calls a given closure with a raw pointer to the multiarray’s storage.

iOS 15.4+iPadOS 15.4+Mac Catalyst 15.4+macOS 12.3+tvOS 15.4+visionOS 1.0+watchOS 8.5+

``` source
func withUnsafeBufferPointer(
    ofType type: S.Type,
    _ body: (UnsafeBufferPointer) throws -> R
) rethrows -> R where S : MLShapedArrayScalar
```

## Parameters 

`type`  

The element type of the buffer passed in the body. This must be a Swift primitive type equivalent to `dataType`. This closure takes the following parameter:

`ptr`  
The pointer to the buffer.

`body`  

A closure with an UnsafeBufferPointer parameter that points to the storage for the multiarray.

## Discussion

The buffer contains a collection of `int32`, `float16`, `float32`, or `float64` values, depending on the multiarray’s data type. It may not store these scalar values contiguously; use strides to get the buffer layout.

## See Also

### Providing buffer access

func withUnsafeBytes&lt;R>((UnsafeRawBufferPointer) throws -> R) rethrows -> R

Calls a given closure with a raw pointer to the multiarray’s storage.

func withUnsafeMutableBufferPointer&lt;S, R>(ofType: S.Type, (UnsafeMutableBufferPointer&lt;S>, [Int]) throws -> R) rethrows -> R

Calls a given closure with a raw pointer to the multiarray’s mutable storage.

func withUnsafeMutableBytes&lt;R>((UnsafeMutableRawBufferPointer, [Int]) throws -> R) rethrows -> R

Calls a given closure with a raw pointer to the multiarray’s mutable storage.

