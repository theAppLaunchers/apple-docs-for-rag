

- Accelerate
-  cblas_dtpsv(\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# cblas_dtpsv(\_:\_:\_:\_:\_:\_:\_:\_:)

Solves a packed triangular system of equations.

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+tvOS 16.4+visionOS 1.0+watchOS 9.4+

``` source
func cblas_dtpsv(
    _ ORDER: CBLAS_ORDER,
    _ UPLO: CBLAS_UPLO,
    _ TRANSA: CBLAS_TRANSPOSE,
    _ DIAG: CBLAS_DIAG,
    _ N: __LAPACK_int,
    _ AP: UnsafePointer?,
    _ X: UnsafeMutablePointer?,
    _ INCX: __LAPACK_int
)
```

## Parameters 

`ORDER`  

Specifies row-major (C) or column-major (Fortran) data ordering.

`UPLO`  

Specifies whether to use the upper or lower triangle from the matrix. Valid values are `'U'` or `'L'`.

`TRANSA`  

Specifies whether to use matrix A (`'N'` or `'n'`) or the transpose of A (`'T'`, `'t'`, `'C'`, or `'c'`).

`DIAG`  

Specifies whether the matrix is unit triangular. Possible values are `'U'` (unit triangular) or `'N'` (not unit triangular).

`N`  

Order of matrix `A`.

`AP`  

Matrix `A` (in packed storage format).

`X`  

Contains vector `B` on entry. Overwritten with vector `X` on return.

`INCX`  

Stride within `X`. For example, if `incX` is 7, every 7th element is used.

## Discussion

Solves the system of equations `A*X=B` or `A'*X=B`, depending on the value of `TransA`.

Important

Apple provides the BLAS and LAPACK libraries under the Accelerate framework to be in line with LAPACK 3.9.1. Starting with iOS 18, iPadOS 18, macOS 15, tvOS 18, watchOS 18, and visionOS 2, the libraries are in line with LAPACK 3.11.0. These new interfaces provide additional functionality, as well as a new ILP64 interface. To use the new interfaces, define `ACCELERATE_NEW_LAPACK` before including the Accelerate or vecLib headers. For ILP64 interfaces, also define `ACCELERATE_LAPACK_ILP64`. For Swift projects, specify `ACCELERATE_NEW_LAPACK=1` and `ACCELERATE_LAPACK_ILP64=1` as preprocessor macros in Xcode build settings.

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

