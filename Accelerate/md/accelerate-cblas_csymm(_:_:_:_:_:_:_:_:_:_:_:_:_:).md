

- Accelerate
-  cblas_csymm(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# cblas_csymm(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:)

Multiplies a matrix by a symmetric matrix (single-precision complex).

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+tvOS 16.4+visionOS 1.0+watchOS 9.4+

``` source
func cblas_csymm(
    _ ORDER: CBLAS_ORDER,
    _ SIDE: CBLAS_SIDE,
    _ UPLO: CBLAS_UPLO,
    _ M: __LAPACK_int,
    _ N: __LAPACK_int,
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

### Single-precision complex matrix functions

func cblas_caxpy(__LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Computes a constant times a vector plus a vector (single-precision complex).

func cblas_ccopy(__LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Copies a vector to another vector (single-precision complex).

func cblas_cgbmv(CBLAS_ORDER, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Scales a general band matrix, then multiplies by a vector, then adds a vector (single-precision complex).

func cblas_cgemm(CBLAS_ORDER, CBLAS_TRANSPOSE, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Multiplies two matrices (single-precision complex).

func cblas_cgemv(CBLAS_ORDER, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Multiplies a matrix by a vector (single-precision complex).

func cblas_cgerc(CBLAS_ORDER, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Multiplies vector X by the conjugate transpose of vector Y, then adds matrix A (single-precision complex).

func cblas_cgeru(CBLAS_ORDER, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Multiplies vector X by the transpose of vector Y, then adds matrix A (single-precision complex).

func cblas_chbmv(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Scales a Hermitian band matrix, then multiplies by a vector, then adds a vector (single-precision complex).

func cblas_chemm(CBLAS_ORDER, CBLAS_SIDE, CBLAS_UPLO, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Multiplies two Hermitian matrices (single-precision complex), then adds a third (with scaling).

func cblas_chemv(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Scales and multiplies a Hermitian matrix by a vector, then adds a second (scaled) vector.

func cblas_cher(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, Float, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Hermitian rank 1 update: adds the product of a scaling factor, vector `X`, and the conjugate transpose of `X` to matrix `A`.

func cblas_cher2(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int)

Hermitian rank 2 update: adds the product of a scaling factor, vector `X`, and the conjugate transpose of vector `Y` to the product of the conjugate of the scaling factor, vector `Y`, and the conjugate transpose of vector `X`, and adds the result to matrix `A`.

func cblas_cher2k(CBLAS_ORDER, CBLAS_UPLO, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int, OpaquePointer?, __LAPACK_int, Float, OpaquePointer?, __LAPACK_int)

Performs a rank-2k update of a complex Hermitian matrix (single-precision complex).

func cblas_cherk(CBLAS_ORDER, CBLAS_UPLO, CBLAS_TRANSPOSE, __LAPACK_int, __LAPACK_int, Float, OpaquePointer?, __LAPACK_int, Float, OpaquePointer?, __LAPACK_int)

Rank-k update—multiplies a Hermitian matrix by its transpose and adds a second matrix (single precision).

func cblas_chpmv(CBLAS_ORDER, CBLAS_UPLO, __LAPACK_int, OpaquePointer, OpaquePointer?, OpaquePointer?, __LAPACK_int, OpaquePointer, OpaquePointer?, __LAPACK_int)

Scales a packed hermitian matrix, multiplies it by a vector, and adds a scaled vector.

