

- Accelerate
-  cblas_zgemm(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# cblas_zgemm(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:)

Multiplies two matrices (double-precision complex).

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+tvOS 16.4+visionOS 1.0+watchOS 9.4+

``` source
func cblas_zgemm(
    _ ORDER: CBLAS_ORDER,
    _ TRANSA: CBLAS_TRANSPOSE,
    _ TRANSB: CBLAS_TRANSPOSE,
    _ M: __LAPACK_int,
    _ N: __LAPACK_int,
    _ K: __LAPACK_int,
    _ ALPHA: OpaquePointer,
    _ A: OpaquePointer?,
    _ LDA: __LAPACK_int,
    _ B: OpaquePointer?,
    _ LDB: __LAPACK_int,
    _ BETA: OpaquePointer,
    _ C: OpaquePointer?,
    _ LDC: __LAPACK_int
)
```

## Parameters 

`ORDER`  

Specifies row-major (C) or column-major (Fortran) data ordering.

`TRANSA`  

Specifies whether to transpose matrix `A`.

`TRANSB`  

Specifies whether to transpose matrix `B`.

`M`  

Number of rows in matrices `A` and `C`.

`N`  

Number of columns in matrices `B` and `C`.

`K`  

Number of columns in matrix `A`; number of rows in matrix `B`.

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

This function multiplies `A * B` and multiplies the resulting matrix by `alpha`. It then multiplies matrix `C` by `beta`. It stores the sum of these two products in matrix `C`.

Thus, it calculates either

`C←αAB + βC`

or

`C←αBA + βC`

with optional use of transposed forms of `A`, `B`, or both.

Important

Apple provides the BLAS and LAPACK libraries under the Accelerate framework to be in line with LAPACK 3.9.1. Starting with iOS 18, iPadOS 18, macOS 15, tvOS 18, watchOS 18, and visionOS 2, the libraries are in line with LAPACK 3.11.0. These new interfaces provide additional functionality, as well as a new ILP64 interface. To use the new interfaces, define `ACCELERATE_NEW_LAPACK` before including the Accelerate or vecLib headers. For ILP64 interfaces, also define `ACCELERATE_LAPACK_ILP64`. For Swift projects, specify `ACCELERATE_NEW_LAPACK=1` and `ACCELERATE_LAPACK_ILP64=1` as preprocessor macros in Xcode build settings.

## See Also

### Double-precision complex matrix functions

func cblas_dzasum(__LAPACK_int, OpaquePointer?, __LAPACK_int) -> Double

Computes the sum of the absolute values of real and imaginary parts of elements in a vector (single-precision complex).

func cblas_dznrm2(__LAPACK_int, OpaquePointer?, __LAPACK_int) -> Double

Computes the unitary norm of a vector (double-precision complex).

func cblas_zaxpy(__LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Computes a constant times a vector plus a vector (double-precision complex).

func cblas_zcopy(__LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Copies a vector to another vector (double-precision complex).

func cblas_zdrot(__LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, Double, Double)

Applies a Givens rotation matrix to a pair of complex vectors.

func cblas_zdscal(__LAPACK_int, Double, OpaquePointer?, __LAPACK_int)

Multiplies each element of a vector by a constant (double-precision complex).

func cblas_zgbmv(CBLAS_ORDER, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Scales a general band matrix, then multiplies by a vector, then adds a vector (double-precision complex).

func cblas_zgemv(CBLAS_ORDER, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Multiplies a matrix by a vector (double-precision complex).

func cblas_zgerc(CBLAS_ORDER, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Multiplies vector X by the conjugate transpose of vector Y, then adds matrix A (double-precision complex).

func cblas_zgeru(CBLAS_ORDER, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Multiplies vector X by the transpose of vector Y, then adds matrix A (double-precision complex).

func cblas_zhbmv(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Scales a Hermitian band matrix, then multiplies by a vector, then adds a vector (double-precision complex).

func cblas_zhemm(CBLAS_ORDER, CBLAS_SIDE, CBLAS_UPLO, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Multiplies two Hermitian matrices (double-precision complex).

func cblas_zhemv(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Scales and multiplies a Hermitian matrix by a vector, then adds a second (scaled) vector.

func cblas_zher(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, Double, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Adds the product of a scaling factor, vector `X`, and the conjugate transpose of `X` to matrix `A`.

func cblas_zher2(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Hermitian rank 2 update: adds the product of a scaling factor, vector `X`, and the conjugate transpose of vector `Y` to the product of the conjugate of the scaling factor, vector `Y`, and the conjugate transpose of vector `X`, and adds the result to matrix `A`.

