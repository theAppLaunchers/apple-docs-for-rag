*   [Core ML](/documentation/coreml)
*   MLShapedArray

Structure

# MLShapedArray

A machine learning collection type that stores scalar values in a multidimensional array.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct MLShapedArray<Scalar> where Scalar : [`MLShapedArrayScalar`](/documentation/coreml/mlshapedarrayscalar)
```
```
```
```
```
```
```
```

## [Overview](/documentation/CoreML/MLShapedArray#overview)

A shaped array is a multidimensional array type that’s the Swift counterpart to [`MLMultiArray`](/documentation/coreml/mlmultiarray). [`MLShapedArray`](/documentation/coreml/mlshapedarray) is one of the underlying types of `MLFeatureValue` that stores scalar values. You can convert a shaped array to an [`MLMultiArray`](/documentation/coreml/mlmultiarray) with its [`init(_:)`](/documentation/coreml/mlmultiarray/init\(_:\)-wk41) initializer, and convert back to a shaped array with its [`init(_:)`](/documentation/coreml/mlshapedarray/init\(_:\)) initializer. All elements in an [`MLShapedArray`](/documentation/coreml/mlshapedarray) are of the same type, and that type must conform to [`MLShapedArrayScalar`](/documentation/coreml/mlshapedarrayscalar):

*   [`Int32`](/documentation/Swift/Int32)
    
*   [`Float`](/documentation/Swift/Float)
    
*   [`Double`](/documentation/Swift/Double)
    

Each dimension in a shaped array is typically significant or meaningful. For example, a model could have an input that accepts images as a three-dimensional array of pixels, C x H x W. The first dimension, _C_,\_ \_represents the number of color channels, and the second and third dimensions, _H_ and _W_, represent the image’s height and width, respectively. The number of dimensions and size of each dimension define the shaped array’s _shape_.

Note

Some models use a one-dimensional multiarray for an input or output. This type of shaped array is conceptually identical to a conventional [`Array`](/documentation/Swift/Array).

A shaped array’s [`shape`](/documentation/coreml/mlmultiarray/shape) property is an integer array in which each element defines the size of the corresponding dimension. To inspect the shape and constraints of a model’s multiarray input or output feature:

1.  Access the model’s [`modelDescription`](/documentation/coreml/mlmodel/modeldescription) property.
    
2.  Find the multiarray input or output feature in the model description’s [`inputDescriptionsByName`](/documentation/coreml/mlmodeldescription/inputdescriptionsbyname) or [`outputDescriptionsByName`](/documentation/coreml/mlmodeldescription/outputdescriptionsbyname) property, respectively.
    
3.  Access the feature description’s [`multiArrayConstraint`](/documentation/coreml/mlfeaturedescription/multiarrayconstraint) property.
    
4.  Inspect the multiarray constraint’s [`shape`](/documentation/coreml/mlmultiarrayconstraint/shape) and [`shapeConstraint`](/documentation/coreml/mlmultiarrayconstraint/shapeconstraint).
    

## [Topics](/documentation/CoreML/MLShapedArray#topics)

### [Creating a Shaped Array](/documentation/CoreML/MLShapedArray#Creating-a-Shaped-Array)

[`init(scalar: Scalar)`](/documentation/coreml/mlshapedarray/init\(scalar:\))

Creates a shaped array with exactly one value and zero dimensions.

[`init<S>(scalars: S, shape: [Int])`](/documentation/coreml/mlshapedarray/init\(scalars:shape:\))

Initialize with a sequence and the shape.

### [Creating a Shaped Array from Another Type](/documentation/CoreML/MLShapedArray#Creating-a-Shaped-Array-from-Another-Type)

[`init(MLMultiArray)`](/documentation/coreml/mlshapedarray/init\(_:\))

[`init<S>(concatenating: S, alongAxis: Int)`](/documentation/coreml/mlshapedarray/init\(concatenating:alongaxis:\))

Merges a sequence of shaped arrays into one shaped array along an axis.

### [Creating a shaped array with pointers to memory](/documentation/CoreML/MLShapedArray#Creating-a-shaped-array-with-pointers-to-memory)

[`init(unsafeUninitializedShape: [Int], initializingWith: (inout UnsafeMutableBufferPointer<Scalar>, [Int]) throws -> Void) rethrows`](/documentation/coreml/mlshapedarray/init\(unsafeuninitializedshape:initializingwith:\))

Creates a shaped array from a shape and a closure that initializes its memory.

### [Creating a shaped array from data](/documentation/CoreML/MLShapedArray#Creating-a-shaped-array-from-data)

[`init(data: Data, shape: [Int])`](/documentation/coreml/mlshapedarray/init\(data:shape:\))

Creates a shaped array from a block of data and a shape.

[`init(data: Data, shape: [Int], strides: [Int])`](/documentation/coreml/mlshapedarray/init\(data:shape:strides:\))

Creates a shaped array from a block of data, a shape, and strides.

### [Encoding and decoding](/documentation/CoreML/MLShapedArray#Encoding-and-decoding)

[`init(from: any Decoder) throws`](/documentation/coreml/mlshapedarray/init\(from:\))

Creates a shaped array from a decoder.

```swift
```swift
```swift
func encode(to: any Encoder) throws
```
```

Encode a shaped array.
```

### [Inspecting a Shaped Array](/documentation/CoreML/MLShapedArray#Inspecting-a-Shaped-Array)

```swift
```swift
```swift
```swift
var description: String
```
```

A text representation of the shaped array.
```
```

### [Supporting Types](/documentation/CoreML/MLShapedArray#Supporting-Types)

[

API Reference

Shaped Array Collection Operations](/documentation/coreml/shaped-array-collection-operations)

Properties and methods a shaped array inherits from collection protocols.

### [Initializers](/documentation/CoreML/MLShapedArray#Initializers)

[`init(mutating: CVPixelBuffer, shape: [Int])`](/documentation/coreml/mlshapedarray/init\(mutating:shape:\))

Creates a new `MLShapedArray` using a pixel buffer as the backing storage.

### [Instance Methods](/documentation/CoreML/MLShapedArray#Instance-Methods)

```swift
```swift
```swift
```swift
func changingLayout(to: MLShapedArrayBufferLayout) -> MLShapedArray<Scalar>
```
```

Returns a copy with the specified buffer layout.
```
```swift
```swift
```swift
func expandingShape(at: Int) -> MLShapedArray<Scalar>
```
```

Returns a new shaped array with expanded dimensions.
```
```swift
```swift
```swift
func reshaped(to: [Int]) -> MLShapedArray<Scalar>
```
```

Returns a new reshaped shaped array.
```
```swift
```swift
```swift
func squeezingShape() -> MLShapedArray<Scalar>
```
```

Returns a new squeezed shaped array.
```
```swift
```swift
```swift
func transposed() -> MLShapedArray<Scalar>
```
```

Returns a new transposed shaped array.
```
```swift
```swift
```swift
func transposed(permutation: [Int]) -> MLShapedArray<Scalar>
```
```

Returns a transposed shaped array using a custom permutation.
```
```swift
```swift
```swift
func withMutablePixelBufferIfAvailable<R>((CVPixelBuffer) throws -> R) rethrows -> R?
```
```

Writes to the underlying pixel buffer.
```
```swift
```swift
```swift
func withPixelBufferIfAvailable<R>((CVPixelBuffer) throws -> R) rethrows -> R?
```
```

Reads the underlying pixel buffer.
```
```swift
```swift
```swift
func withUnsafeMutableShapedBufferPointer<R>(using: MLShapedArrayBufferLayout, (inout UnsafeMutableBufferPointer<Scalar>, [Int], [Int]) throws -> R) rethrows -> R
```
```

Calls the given closure with a pointer to the array’s mutable storage that has a specified buffer layout.
```
```

### [Default Implementations](/documentation/CoreML/MLShapedArray#Default-Implementations)

[

API Reference

CustomStringConvertible Implementations](/documentation/coreml/mlshapedarray/customstringconvertible-implementations)

[

API Reference

Decodable Implementations](/documentation/coreml/mlshapedarray/decodable-implementations)

[

API Reference

Encodable Implementations](/documentation/coreml/mlshapedarray/encodable-implementations)

## [Relationships](/documentation/CoreML/MLShapedArray#relationships)

### [Conforms To](/documentation/CoreML/MLShapedArray#conforms-to)

*   [`BidirectionalCollection`](/documentation/Swift/BidirectionalCollection)
*   [`Collection`](/documentation/Swift/Collection)
*   [`Copyable`](/documentation/Swift/Copyable)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Decodable`](/documentation/Swift/Decodable)
*   [`Encodable`](/documentation/Swift/Encodable)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`ExpressibleByArrayLiteral`](/documentation/Swift/ExpressibleByArrayLiteral)
*   [`MLShapedArrayProtocol`](/documentation/coreml/mlshapedarrayprotocol)
*   [`MutableCollection`](/documentation/Swift/MutableCollection)
*   [`RandomAccessCollection`](/documentation/Swift/RandomAccessCollection)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`Sequence`](/documentation/Swift/Sequence)

## [See Also](/documentation/CoreML/MLShapedArray#see-also)

### [Supporting Types](/documentation/CoreML/MLShapedArray#Supporting-Types)

```swift
```swift
```swift
```swift
enum MLFeatureType
```
```

The possible types for feature values, input features, and output features.
```
```swift
```swift
```swift
protocol MLShapedArrayProtocol
```
```

An interface that defines a shaped array type.
```
```swift
```swift
```swift
class MLMultiArray
```
```

A machine learning collection type that stores numeric values in an array with multiple dimensions.
```
```swift
```swift
```swift
class MLSequence
```
```

A machine learning collection type that stores a series of strings or integers.
```
```