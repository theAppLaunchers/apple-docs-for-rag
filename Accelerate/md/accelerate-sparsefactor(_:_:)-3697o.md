

- Accelerate
-  SparseFactor(\_:\_:) 

Function

# SparseFactor(\_:\_:)

Returns a symbolic factorization of the requested type for a specified sparsity structure.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
func SparseFactor(
    _ type: SparseFactorization_t,
    _ Matrix: SparseMatrixStructure
) -> SparseOpaqueSymbolicFactorization
```

## Parameters 

`type`  

The factorization type.

`Matrix`  

The matrix to factorize.

## Return Value

A SparseOpaqueSymbolicFactorization structure that represents the symbolic factorization.

## Discussion

Use this function to calculate the symbolic factorization of a sparse matrix’s structure to pass to the direct solve functions. You can use the symbolic factorization that this function returns for multiple numerical factorizations with different numerical values and different precisions, but the same nonzero structure.

The following figure shows two systems of equations where the coefficient matrix is sparse:

The following code solves these two systems by creating a symbolic factorization that’s common to both coefficient matrices. Note that the two coefficient matrices contain different numeric values with different precisions.

```
/// Define the sparsity pattern of matrices `A0` and `A1`.
let rowIndices: [Int32] =    [ 0, 1, 1, 2]
let columnIndices: [Int32] = [ 2, 0, 2, 1]

/// Create the single-precision coefficient matrix _A0_.
let a0Values: [Float] = [10, 20, 5, 50]
let A0 = SparseConvertFromCoordinate(3, 3,
                                     4, 1,
                                     SparseAttributes_t(),
                                     rowIndices, columnIndices,
                                     a0Values)

/// Create the double-precision coefficient matrix _A1_.
let a1Values: [Double] = [5, 10, 2.5, 25]
let A1 = SparseConvertFromCoordinate(3, 3,
                                     4, 1,
                                     SparseAttributes_t(),
                                     rowIndices, columnIndices,
                                     a1Values)

/// Compute the symbolic factorization from the structure of either coefficient matrix.
let structure = A0.structure
let symbolicFactorization = SparseFactor(SparseFactorizationQR,
                                         structure)

/// Factorize _A0_ using the symbolic factorization.
let factorization0 = SparseFactor(symbolicFactorization, A0)

/// Solve _A0 · x = b0_ in place.
var b0Values: [Float] = [30, 35, 100]
b0Values.withUnsafeMutableBufferPointer { bPtr in
    let xb = DenseVector_Float(count: 3,
                               data: bPtr.baseAddress!)

    SparseSolve(factorization0, xb)
}

/// Factorize _A1_ using the symbolic factorization.
let factorization1 = SparseFactor(symbolicFactorization, A1)

/// Solve _A1 · x = b1_ in place.
var b1Values: [Double] = [60, 70, 200]
b1Values.withUnsafeMutableBufferPointer { bPtr in
    let xb = DenseVector_Double(count: 3,
                               data: bPtr.baseAddress!)

    SparseSolve(factorization1, xb)
}

SparseCleanup(A0)
SparseCleanup(A1)
SparseCleanup(factorization0)
SparseCleanup(factorization1)
```

On return, `b0Values` contains the values `[1.0, 2.0, 3.0]`, and `b1Values` contains the values `[4.0, 8.0, 12.0]`.

## See Also

### Matrix Symbolic Factorization Functions

func SparseFactor(SparseFactorization_t, SparseMatrixStructure, SparseSymbolicFactorOptions) -> SparseOpaqueSymbolicFactorization

Returns a symbolic factorization of the requested type for a single-precision matrix with the specified structure.

