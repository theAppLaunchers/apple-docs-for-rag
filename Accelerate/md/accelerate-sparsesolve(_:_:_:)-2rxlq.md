

- Accelerate
-  SparseSolve(\_:\_:\_:) 

Function

# SparseSolve(\_:\_:\_:)

Solves the system *AX = B* using the supplied single-precision factorization of *A*.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
func SparseSolve(
    _ Factored: SparseOpaqueFactorization_Float,
    _ B: DenseMatrix_Float,
    _ X: DenseMatrix_Float
)
```

## Parameters 

`Factored`  

The factorization of *A*.

`B`  

The right-hand-side, B.

`X`  

The matrix for returning solutions.

## Discussion

Use this function to solve a system of linear equations using a factored coefficient matrix. The following figure shows two systems of equations where the coefficient matrix is sparse:

The following code solves this system with a QR factorization of the coefficient matrix:

```
/// Create the coefficient matrix _A_.
let rowIndices: [Int32] =    [ 0,  1, 1,  2]
let columnIndices: [Int32] = [ 2,  0, 2,  1]
let aValues: [Float] =       [10, 20, 5, 50]

let A = SparseConvertFromCoordinate(3, 3,
                                    4, 1,
                                    SparseAttributes_t(),
                                    rowIndices, columnIndices,
                                    aValues)

/// Factorize _A_.
let factorization = SparseFactor(SparseFactorizationQR, A)

defer {
    SparseCleanup(A)
    SparseCleanup(factorization)
}

/// Create the right-hand-side matrix, _b_.
var bValues: [Float] = [30, 35, 100,
                        300, 350, 1000]
let n = bValues.count

/// Solve the system.
let xValues = [Float](unsafeUninitializedCapacity: n) {
    buffer, count in
    bValues.withUnsafeMutableBufferPointer { bPtr in
        let B = DenseMatrix_Float(rowCount: 3,
                                  columnCount: 2,
                                  columnStride: 3,
                                  attributes: SparseAttributes_t(),
                                  data: bPtr.baseAddress!)

        let X = DenseMatrix_Float(rowCount: 3,
                                  columnCount: 2,
                                  columnStride: 3,
                                  attributes: SparseAttributes_t(),
                                  data: buffer.baseAddress!)

        SparseSolve(factorization, B, X)

        count = n
    }
}
```

On return, `xValues` contains the values `[1.0, 2.0, 3.0, 10.0, 20.0, 30.0]`.

If the factorization is *A = QR*, the function returns the solution of minimum norm *‖ x ‖₂* for underdetermined systems.

If the factorization is *A = QR*, the function returns the least squares solution *minₓ ‖ AX - B ‖₂* for overdetermined systems.

If the factorization is SparseFactorizationCholeskyAtA, the factorization is of *AᵀA*, and the solution that returns is for the system *AᵀAX = B*.

## See Also

### Out-of-Place Direct Solving Functions

func SparseSolve(SparseOpaqueFactorization_Double, DenseMatrix_Double, DenseMatrix_Double)

Solves the system *AX = B* using the supplied double-precision factorization of *A*.

