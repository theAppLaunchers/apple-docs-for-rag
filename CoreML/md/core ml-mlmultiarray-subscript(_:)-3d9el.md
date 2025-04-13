

- Core ML
- MLMultiArray
-  subscript(\_:) 

Instance Subscript

# subscript(\_:)

Accesses the multiarray by using a number array that has an element for each dimension.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.0+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
subscript(key: [NSNumber]) -> NSNumber { get set }
```

## Parameters 

`key`  

An NSNumber array that represents a position in a multiarray in which each element is an index in the corresponding dimension.

## Return Value

A number.

## Discussion

Use this subscript to access the multiarray by using an NSNumber array in which each element is an index in the multiarray’s corresponding dimension.

```
// A multiarray with three dimensions.
let multiarray = try MLMultiArray(shape: [5, 29, 17], dataType: .double)

// The subscript key with three elements.
let key = [3, 5, 7] as [NSNumber]

// Set the element to π, a sentinel value.
multiarray[key] = 3.141_59

// Retrieve the element as a number.
let numberValue = multiarray[key]
print(numberValue.doubleValue)
// Prints: 3.14159
```

For better performance, directly access the multiarray’s underlying pointer by using a linear offset. Calculate the linear offset by summing the products of each dimension’s index with the dimension’s stride (See strides).

```
// Get a pointer to the multiarray’s contents.
let pointer = UnsafeMutablePointer(OpaquePointer(multiarray.dataPointer))
var linearOffset = 0

// Sum the products of each dimension’s number with its stride.
for (dimension, stride) in zip(key, multiarray.strides) {
    linearOffset += dimension.intValue * stride.intValue
}

// Check that the linear offset resolves to the same element as the subscript.
assert(pointer[linearOffset] == multiarray[key].doubleValue)

print(pointer[linearOffset])
// Prints: 3.14159

// Set the element to a different sentinel value.
pointer[linearOffset] = 2.718_28
print(pointer[linearOffset])
// Prints: 2.71828
```

## See Also

### Accessing a Multiarray’s Elements

subscript(Int) -> NSNumber

Accesses the multiarray by using a linear offset.

var pixelBuffer: CVPixelBuffer?

A reference to the multiarray’s underlying pixel buffer.

var dataPointer: UnsafeMutableRawPointer

A pointer to the multiarray’s underlying memory.

Deprecated

