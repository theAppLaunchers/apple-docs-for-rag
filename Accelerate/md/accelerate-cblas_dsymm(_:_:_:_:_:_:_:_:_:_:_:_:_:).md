

- Accelerate
-  cblas_dsymm(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# cblas_dsymm(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:)

Multiplies a matrix by a symmetric matrix (double-precision).

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+tvOS 16.4+visionOS 1.0+watchOS 9.4+

``` source
func cblas_dsymm(
    _ ORDER: CBLAS_ORDER,
    _ SIDE: CBLAS_SIDE,
    _ UPLO: CBLAS_UPLO,
    _ M: __LAPACK_int,
    _ N: __LAPACK_int,
    _ ALPHA: Double,
    _ A: UnsafePointer?,
    _ LDA: __LAPACK_int,
    _ B: UnsafePointer?,
    _ LDB: __LAPACK_int,
    _ BETA: Double,
    _ C: UnsafeMutablePointer?,
    _ LDC: __LAPACK_int
)
```

## Parameters 

`ORDER`  

Specifies row-major (C) or column-major (Fortran) data ordering.

`SIDE`  

Determines the order in which the matrices should be multiplied.

`UPLO`  

Specifies whether to use the upper or lower triangle from the matrix. Valid values are `'U'` or `'L'`.

`M`  

Number of rows in matrices `A` and `C`.

`N`  

Number of columns in matrices `B` and `C`.

`ALPHA`  

Scaling factor for the product of matrices A and B.

`A`  

Matrix A.

`LDA`  

The size of the first dimension of matrix `A`; if you are passing a matrix `A[m][n]`, the value should be `m`.

`B`  

Matrix B.

`LDB`  

The size of the first dimension of matrix `B`; if you are passing a matrix `B[m][n]`, the value should be `m`.

`BETA`  

Scaling factor for matrix C.

`C`  

Matrix C.

`LDC`  

The size of the first dimension of matrix `C`; if you are passing a matrix `C[m][n]`, the value should be `m`.

## Discussion

This function multiplies `A * B` or `B * A` (depending on the value of `Side`) and multiplies the resulting matrix by `alpha`. It then multiplies matrix `C` by `beta`. It stores the sum of these two products in matrix `C`.

Thus, it calculates either

`C←αAB + βC`

or

`C←αBA + βC`

where

`A = A`

Important

Apple provides the BLAS and LAPACK libraries under the Accelerate framework to be in line with LAPACK 3.9.1. Starting with iOS 18, iPadOS 18, macOS 15, tvOS 18, watchOS 18, and visionOS 2, the libraries are in line with LAPACK 3.11.0. These new interfaces provide additional functionality, as well as a new ILP64 interface. To use the new interfaces, define `ACCELERATE_NEW_LAPACK` before including the Accelerate or vecLib headers. For ILP64 interfaces, also define `ACCELERATE_LAPACK_ILP64`. For Swift projects, specify `ACCELERATE_NEW_LAPACK=1` and `ACCELERATE_LAPACK_ILP64=1` as preprocessor macros in Xcode build settings.

\`\`

## See Also

### Double-precision float matrix functions

func cblas_dasum(__LAPACK_int, UnsafePointer&lt;Double>?, __LAPACK_int) -> Double

Computes the sum of the absolute values of elements in a vector (double-precision).

func cblas_daxpy(__LAPACK_int, Double, UnsafePointer&lt;Double>?, __LAPACK_int, UnsafeMutablePointer&lt;Double>?, __LAPACK_int)

Computes a constant times a vector plus a vector (double-precision).

func cblas_dcopy(__LAPACK_int, UnsafePointer&lt;Double>?, __LAPACK_int, UnsafeMutablePointer&lt;Double>?, __LAPACK_int)

Copies a vector to another vector (double-precision).

func cblas_dgbmv(CBLAS_ORDER, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, __LAPACK_int, __LAPACK_int, Double, UnsafePointer&lt;Double>?, __LAPACK_int, UnsafePointer&lt;Double>?, __LAPACK_int, Double, UnsafeMutablePointer&lt;Double>?, __LAPACK_int)

Scales a general band matrix, then multiplies by a vector, then adds a vector (double precision).

func cblas_dgemm(CBLAS_ORDER, CBLAS_TRANSPOSE, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, __LAPACK_int, Double, UnsafePointer&lt;Double>?, __LAPACK_int, UnsafePointer&lt;Double>?, __LAPACK_int, Double, UnsafeMutablePointer&lt;Double>?, __LAPACK_int)

Multiplies two matrices (double-precision).

func cblas_dgemv(CBLAS_ORDER, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, Double, UnsafePointer&lt;Double>?, __LAPACK_int, UnsafePointer&lt;Double>?, __LAPACK_int, Double, UnsafeMutablePointer&lt;Double>?, __LAPACK_int)

Multiplies a matrix by a vector (double precision).

func cblas_dger(CBLAS_ORDER, __LAPACK_int, __LAPACK_int, Double, UnsafePointer&lt;Double>?, __LAPACK_int, UnsafePointer&lt;Double>?, __LAPACK_int, UnsafeMutablePointer&lt;Double>?, __LAPACK_int)

Multiplies vector X by the transpose of vector Y, then adds matrix A (double precison).

func cblas_dnrm2(__LAPACK_int, UnsafePointer&lt;Double>?, __LAPACK_int) -> Double

Computes the L2 norm (Euclidian length) of a vector (double precision).

func cblas_drot(__LAPACK_int, UnsafeMutablePointer&lt;Double>?, __LAPACK_int, UnsafeMutablePointer&lt;Double>?, __LAPACK_int, Double, Double)

Applies a Givens rotation matrix to a pair of vectors.

func cblas_drotg(UnsafeMutablePointer&lt;Double>, UnsafeMutablePointer&lt;Double>, UnsafeMutablePointer&lt;Double>, UnsafeMutablePointer&lt;Double>)

Constructs a Givens rotation matrix.

func cblas_drotm(__LAPACK_int, UnsafeMutablePointer&lt;Double>?, __LAPACK_int, UnsafeMutablePointer&lt;Double>?, __LAPACK_int, UnsafePointer&lt;Double>)

Applies a modified Givens transformation (single precision).

func cblas_drotmg(UnsafeMutablePointer&lt;Double>, UnsafeMutablePointer&lt;Double>, UnsafeMutablePointer&lt;Double>, Double, UnsafeMutablePointer&lt;Double>)

Generates a modified Givens rotation matrix.

func cblas_dsbmv(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, __LAPACK_int, Double, UnsafePointer&lt;Double>?, __LAPACK_int, UnsafePointer&lt;Double>?, __LAPACK_int, Double, UnsafeMutablePointer&lt;Double>?, __LAPACK_int)

Scales a symmetric band matrix, then multiplies by a vector, then adds a vector (double precision).

func cblas_dscal(__LAPACK_int, Double, UnsafeMutablePointer&lt;Double>?, __LAPACK_int)

Multiplies each element of a vector by a constant (double-precision).

func cblas_dspmv(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, Double, UnsafePointer&lt;Double>?, UnsafePointer&lt;Double>?, __LAPACK_int, Double, UnsafeMutablePointer&lt;Double>?, __LAPACK_int)

Scales a packed symmetric matrix, then multiplies by a vector, then scales and adds another vector (double precision).

