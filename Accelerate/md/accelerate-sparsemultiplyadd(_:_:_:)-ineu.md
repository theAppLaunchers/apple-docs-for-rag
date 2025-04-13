

- Accelerate
-  SparseMultiplyAdd(\_:\_:\_:) 

Function

# SparseMultiplyAdd(\_:\_:\_:)

Performs the multiply operation *y += Ax* on a vector of double-precision, floating-point values.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
func SparseMultiplyAdd(
    _ A: SparseMatrix_Float,
    _ x: DenseVector_Float,
    _ y: DenseVector_Float
)
```

## Parameters 

`A`  

The sparse matrix *A* in *y* *+= Ax*.

`x`  

The dense vector *x* in *y* *+= Ax*.

`y`  

The dense vector *y* in *y* *+= Ax*.

## Discussion

Use this function to multiply a sparse matrix by a dense vector and accumulate the result. The following equation is an example of a matrix-vector multiplication where the matrix is sparse:

Call SparseMultiplyAdd(_:_:_:) to calculate the result.

```
let rowCount = Int32(4)
let columnCount = Int32(4)
let blockCount = 4
let blockSize = UInt8(1)
let rowIndices: [Int32] = [0, 3, 0, 3]
let columnIndices: [Int32] = [0, 0, 3, 3]
let data: [Float] = [1.0, 4.0, 13.0, 16.0]

/// The _A_ in _y+=Ax_.
let A = SparseConvertFromCoordinate(rowCount, columnCount,
                                    blockCount, blockSize,
                                    SparseAttributes_t(),
                                    rowIndices, columnIndices,
                                    data)
defer {
    SparseCleanup(A)
}

/// The values for _x_ in _y+=Ax_.
var xValues: [Float] = [10.0, -1.0, -1.0, 10.0]

var yValues: [Float] = [1.0, 1.0, 1.0, 1.0]

/// The values for _y_ in _y+=Ax_.
yValues.withUnsafeMutableBufferPointer { yValuesPtr in

    xValues.withUnsafeMutableBufferPointer { xValuesPtr in
        /// The _x_ in _y+=Ax_.
        let x = DenseVector_Float(count: 4,
                                  data: xValuesPtr.baseAddress!)

        /// The _y_ in _y+=Ax_.
        let y = DenseVector_Float(count: 4,
                                  data: yValuesPtr.baseAddress!)

        SparseMultiplyAdd(A, x, y)
    }
}

/// On return, `yValues` contains:
///      `[ 141.0, 1.0, 1.0, 201.0 ]`
```

## See Also

### Multiply-Add Functions

func SparseMultiplyAdd(SparseMatrix_Double, DenseVector_Double, DenseVector_Double)

Performs the multiply operation *y += Ax* on a vector of double-precision, floating-point values.

func SparseMultiplyAdd(Double, SparseMatrix_Double, DenseVector_Double, DenseVector_Double)

Performs the multiply operation *y += alpha \* Ax* on a vector of double-precision, floating-point values.

func SparseMultiplyAdd(Float, SparseMatrix_Float, DenseVector_Float, DenseVector_Float)

Performs the multiply operation *y += alpha \* Ax* on a vector of single-precision, floating-point values.

