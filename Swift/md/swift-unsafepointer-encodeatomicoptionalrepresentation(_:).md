

- Swift
- UnsafePointer
-  encodeAtomicOptionalRepresentation(\_:) 

Type Method

# encodeAtomicOptionalRepresentation(\_:)

Destroys a value of `Self` and prepares an `AtomicOptionalRepresentation` storage type to be used for atomic operations on `Optional`.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
static func encodeAtomicOptionalRepresentation(_ value: consuming UnsafePointer?) -> UnsafePointer.AtomicOptionalRepresentation
```

## Parameters 

`value`  

An optional instance of `Self` that’s about to be destroyed to encode an instance of its `AtomicOptionalRepresentation`.

## Return Value

The newly encoded `AtomicOptionalRepresentation` storage.

## Discussion

Note

This is not an atomic operation. This simply encodes the logical type `Self` into its storage representation suitable for atomic operations, `AtomicOptionalRepresentation`.

