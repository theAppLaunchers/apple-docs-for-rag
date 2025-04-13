

- Accelerate
-  cblas_sger(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# cblas_sger(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:)

Multiplies vector X by the transpose of vector Y, then adds matrix A (single precison).

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+tvOS 16.4+visionOS 1.0+watchOS 9.4+

``` source
func cblas_sger(
    _ ORDER: CBLAS_ORDER,
    _ M: __LAPACK_int,
    _ N: __LAPACK_int,
    _ ALPHA: Float,
    _ X: UnsafePointer?,
    _ INCX: __LAPACK_int,
    _ Y: UnsafePointer?,
    _ INCY: __LAPACK_int,
    _ A: UnsafeMutablePointer?,
    _ LDA: __LAPACK_int
)
```

## Parameters 

`ORDER`  

Specifies row-major (C) or column-major (Fortran) data ordering.

`M`  

Number of rows in matrix `A`.

`N`  

Number of columns in matrix `A`.

`ALPHA`  

Scaling factor for vector `X`.

`X`  

Vector `X`.

`INCX`  

Stride within `X`. For example, if `incX` is 7, every 7th element is used.

`Y`  

Vector `Y`.

`INCY`  

Stride within `Y`. For example, if `incY` is 7, every 7th element is used.

`A`  

Matrix `A`.

`LDA`  

Leading dimension of array containing matrix `A`.

## Discussion

Computes `alpha*x*y' + A`.

Important

Apple provides the BLAS and LAPACK libraries under the Accelerate framework to be in line with LAPACK 3.9.1. Starting with iOS 18, iPadOS 18, macOS 15, tvOS 18, watchOS 18, and visionOS 2, the libraries are in line with LAPACK 3.11.0. These new interfaces provide additional functionality, as well as a new ILP64 interface. To use the new interfaces, define `ACCELERATE_NEW_LAPACK` before including the Accelerate or vecLib headers. For ILP64 interfaces, also define `ACCELERATE_LAPACK_ILP64`. For Swift projects, specify `ACCELERATE_NEW_LAPACK=1` and `ACCELERATE_LAPACK_ILP64=1` as preprocessor macros in Xcode build settings.

## See Also

### Single-precision float matrix functions

func cblas_sasum(__LAPACK_int, UnsafePointer&lt;Float>?, __LAPACK_int) -> Float

Computes the sum of the absolute values of elements in a vector (single-precision).

func cblas_saxpy(__LAPACK_int, Float, UnsafePointer&lt;Float>?, __LAPACK_int, UnsafeMutablePointer&lt;Float>?, __LAPACK_int)

Computes a constant times a vector plus a vector (single-precision).

func cblas_scopy(__LAPACK_int, UnsafePointer&lt;Float>?, __LAPACK_int, UnsafeMutablePointer&lt;Float>?, __LAPACK_int)

Copies a vector to another vector (single-precision).

func cblas_sgbmv(CBLAS_ORDER, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, __LAPACK_int, __LAPACK_int, Float, UnsafePointer&lt;Float>?, __LAPACK_int, UnsafePointer&lt;Float>?, __LAPACK_int, Float, UnsafeMutablePointer&lt;Float>?, __LAPACK_int)

Scales a general band matrix, then multiplies by a vector, then adds a vector (single precision).

func cblas_sgemm(CBLAS_ORDER, CBLAS_TRANSPOSE, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, __LAPACK_int, Float, UnsafePointer&lt;Float>?, __LAPACK_int, UnsafePointer&lt;Float>?, __LAPACK_int, Float, UnsafeMutablePointer&lt;Float>?, __LAPACK_int)

Multiplies two matrices (single-precision).

func cblas_sgemv(CBLAS_ORDER, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, Float, UnsafePointer&lt;Float>?, __LAPACK_int, UnsafePointer&lt;Float>?, __LAPACK_int, Float, UnsafeMutablePointer&lt;Float>?, __LAPACK_int)

Multiplies a single-precision matrix by a vector.

func cblas_snrm2(__LAPACK_int, UnsafePointer&lt;Float>?, __LAPACK_int) -> Float

Computes the L2 norm (Euclidian length) of a vector (single precision).

func cblas_srot(__LAPACK_int, UnsafeMutablePointer&lt;Float>?, __LAPACK_int, UnsafeMutablePointer&lt;Float>?, __LAPACK_int, Float, Float)

Applies a Givens rotation matrix to a pair of vectors.

func cblas_srotg(UnsafeMutablePointer&lt;Float>, UnsafeMutablePointer&lt;Float>, UnsafeMutablePointer&lt;Float>, UnsafeMutablePointer&lt;Float>)

Constructs a Givens rotation matrix.

func cblas_srotm(__LAPACK_int, UnsafeMutablePointer&lt;Float>?, __LAPACK_int, UnsafeMutablePointer&lt;Float>?, __LAPACK_int, UnsafePointer&lt;Float>)

Applies a modified Givens transformation (single precision).

func cblas_srotmg(UnsafeMutablePointer&lt;Float>, UnsafeMutablePointer&lt;Float>, UnsafeMutablePointer&lt;Float>, Float, UnsafeMutablePointer&lt;Float>)

Generates a modified Givens rotation matrix.

func cblas_ssbmv(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, __LAPACK_int, Float, UnsafePointer&lt;Float>?, __LAPACK_int, UnsafePointer&lt;Float>?, __LAPACK_int, Float, UnsafeMutablePointer&lt;Float>?, __LAPACK_int)

Scales a symmetric band matrix, then multiplies by a vector, then adds a vector (single-precision).

func cblas_sscal(__LAPACK_int, Float, UnsafeMutablePointer&lt;Float>?, __LAPACK_int)

Multiplies each element of a vector by a constant (single-precision).

func cblas_sspmv(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, Float, UnsafePointer&lt;Float>?, UnsafePointer&lt;Float>?, __LAPACK_int, Float, UnsafeMutablePointer&lt;Float>?, __LAPACK_int)

Scales a packed symmetric matrix, then multiplies by a vector, then scales and adds another vector (single precision).

func cblas_sspr(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, Float, UnsafePointer&lt;Float>?, __LAPACK_int, UnsafeMutablePointer&lt;Float>?)

Rank one update: adds a packed symmetric matrix to the product of a scaling factor, a vector, and its transpose (single precision).

