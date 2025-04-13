

- Accelerate
-  sparse_extract_sparse_column_double(\_:\_:\_:\_:\_:\_:\_:) 

Function

# sparse_extract_sparse_column_double(\_:\_:\_:\_:\_:\_:\_:)

Extracts values from a specified column of a double-precision sparse matrix.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 3.0+

``` source
func sparse_extract_sparse_column_double(
    _ A: sparse_matrix_double!,
    _ column: sparse_index,
    _ row_start: sparse_index,
    _ row_end: UnsafeMutablePointer!,
    _ nz: sparse_dimension,
    _ val: UnsafeMutablePointer!,
    _ indx: UnsafeMutablePointer!
) -> sparse_status
```

## Parameters 

`A`  

The sparse matrix, *A*, which must have been created with sparse_matrix_create_double(_:_:). SPARSE_ILLEGAL_PARAMETER is returned if not met.

`column`  

The column for value extraction.

`row_start`  

The index of the row to start extraction.

`row_end`  

On return, holds the row index of the next nonzero value.

`nz`  

The number of values to extract from `A`. Each of `jndx` and `val` are of size `nz`.

`val`  

Pointer to array to hold the values extracted from the sparse matrix. The value is extracted from the location specified by the corresponding indices of `column` and `jndx`. Must be of size `nz` elements. If less than `nz` nonzero values are found, then the last `nz - actual_nonzero_count` elements of val are untouched.

`indx`  

An array to hold the extracted row indices that correspond to the values in `val`. Note that these indices are relative to the matrix column and not the starting row index specified by ``` row``_start ```. Returned indices are 0 based (first element of pointer is `ptr[0]`). Must be of size `nz` elements.

## Return Value

On success `val` and `jndx` have been updated with the nonzero values of the `column`’th row, `row_end` holds the row index of the next nonzero value, and the number of nonzero values written are returned. If `A` creation requirements are not met, SPARSE_ILLEGAL_PARAMETER is returned and `val` and `jndx` are unchanged.

## Discussion

Extract the first `nz` values of the column beginning at `A[column,row_start]` for the sparse matrix `A`. The number of nonzero values extracted is limited by `nz`, and the number of nonzero’s written to `indx` and `val` are returned. Additionally, the row index of the next nonzero value is returned in `row_end`. For example if `nz` is returned, not all nonzero values have been extracted, and a second extract can start from `row_end`.

Important

Apple provides the BLAS and LAPACK libraries under the Accelerate framework to be in line with LAPACK 3.9.1. Starting with iOS 18, iPadOS 18, macOS 15, tvOS 18, watchOS 18, and visionOS 2, the libraries are in line with LAPACK 3.11.0. These new interfaces provide additional functionality, as well as a new ILP64 interface. To use the new interfaces, define `ACCELERATE_NEW_LAPACK` before including the Accelerate or vecLib headers. For ILP64 interfaces, also define `ACCELERATE_LAPACK_ILP64`. For Swift projects, specify `ACCELERATE_NEW_LAPACK=1` and `ACCELERATE_LAPACK_ILP64=1` as preprocessor macros in Xcode build settings.

## See Also

### Value Extraction

func sparse_extract_sparse_row_double(sparse_matrix_double!, sparse_index, sparse_index, UnsafeMutablePointer&lt;sparse_index>!, sparse_dimension, UnsafeMutablePointer&lt;Double>!, UnsafeMutablePointer&lt;sparse_index>!) -> sparse_status

Extracts values from a specified row of a double-precision sparse matrix.

func sparse_extract_sparse_row_float(sparse_matrix_float!, sparse_index, sparse_index, UnsafeMutablePointer&lt;sparse_index>!, sparse_dimension, UnsafeMutablePointer&lt;Float>!, UnsafeMutablePointer&lt;sparse_index>!) -> sparse_status

Extracts values from a specified row of a single-precision sparse matrix.

func sparse_extract_sparse_column_float(sparse_matrix_float!, sparse_index, sparse_index, UnsafeMutablePointer&lt;sparse_index>!, sparse_dimension, UnsafeMutablePointer&lt;Float>!, UnsafeMutablePointer&lt;sparse_index>!) -> sparse_status

Extracts values from a specified column of a single-precision sparse matrix.

