

- Accelerate
-  sparse_insert_entry_float(\_:\_:\_:\_:) 

Function

# sparse_insert_entry_float(\_:\_:\_:\_:)

Inserts a single scalar entry into a single-precision sparse matrix.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 3.0+

``` source
func sparse_insert_entry_float(
    _ A: sparse_matrix_float!,
    _ val: Float,
    _ i: sparse_index,
    _ j: sparse_index
) -> sparse_status
```

## Parameters 

`A`  

The sparse matrix, *A*, which must have been created with sparse_matrix_create_float(_:_:). SPARSE_ILLEGAL_PARAMETER is returned if not met.

`val`  

The scalar value to insert into the sparse matrix.

`i`  

The row location to insert the value. Indices are 0 based (first element of pointer is `ptr[0]`). Indices expected to be in the bounds of matrix dimensions, undefined behavior if not met.

`j`  

The column location to insert the value. Indices are 0 based (first element of pointer is ptr\[0\]). Indices expected to be in the bounds of matrix dimensions, undefined behavior if not met.

## Return Value

On successful insertion, `A` has been updated with the value and SPARSE_SUCCESS is returned. If `A` creation requirements are not met, SPARSE_ILLEGAL_PARAMETER is returned and `A` is unchanged.

## Discussion

Use to build a sparse matrix by inserting one scalar entry at a time. This function is the equivalent of `A[i,j] = val`.

Note that matrix properties cannot be modified after value insertion begins. This includes properties such as specifying a triangular matrix.

Insertion can be expensive, generally speaking it is best to do a batch update.

Inserted values may be temporarily held internally within the object and only inserted into the sparse format when a later computation triggers a need to insert.

Important

Apple provides the BLAS and LAPACK libraries under the Accelerate framework to be in line with LAPACK 3.9.1. Starting with iOS 18, iPadOS 18, macOS 15, tvOS 18, watchOS 18, and visionOS 2, the libraries are in line with LAPACK 3.11.0. These new interfaces provide additional functionality, as well as a new ILP64 interface. To use the new interfaces, define `ACCELERATE_NEW_LAPACK` before including the Accelerate or vecLib headers. For ILP64 interfaces, also define `ACCELERATE_LAPACK_ILP64`. For Swift projects, specify `ACCELERATE_NEW_LAPACK=1` and `ACCELERATE_LAPACK_ILP64=1` as preprocessor macros in Xcode build settings.

## See Also

### Matrix Creation and Population

func sparse_matrix_create_double(sparse_dimension, sparse_dimension) -> sparse_matrix_double!

Returns a double-precision sparse matrix object.

func sparse_matrix_create_float(sparse_dimension, sparse_dimension) -> sparse_matrix_float!

Returns a single-precision sparse matrix object.

func sparse_insert_entry_double(sparse_matrix_double!, Double, sparse_index, sparse_index) -> sparse_status

Inserts a single scalar entry into a double-precision sparse matrix.

func sparse_insert_entries_double(sparse_matrix_double!, sparse_dimension, UnsafePointer&lt;Double>!, UnsafePointer&lt;sparse_index>!, UnsafePointer&lt;sparse_index>!) -> sparse_status

Inserts a list of scalar entries into a double-precision sparse matrix.

func sparse_insert_entries_float(sparse_matrix_float!, sparse_dimension, UnsafePointer&lt;Float>!, UnsafePointer&lt;sparse_index>!, UnsafePointer&lt;sparse_index>!) -> sparse_status

Inserts a list of scalar entries into a single-precision sparse matrix.

func sparse_insert_col_double(sparse_matrix_double!, sparse_index, sparse_dimension, UnsafePointer&lt;Double>!, UnsafePointer&lt;sparse_index>!) -> sparse_status

Inserts a list of scalar entries into a single column of a double-precision sparse matrix.

func sparse_insert_col_float(sparse_matrix_float!, sparse_index, sparse_dimension, UnsafePointer&lt;Float>!, UnsafePointer&lt;sparse_index>!) -> sparse_status

Inserts a list of scalar entries into a single column of a single-precision sparse matrix.

func sparse_insert_row_double(sparse_matrix_double!, sparse_index, sparse_dimension, UnsafePointer&lt;Double>!, UnsafePointer&lt;sparse_index>!) -> sparse_status

Inserts a list of scalar entries into a single row of a double-precision sparse matrix.

func sparse_insert_row_float(sparse_matrix_float!, sparse_index, sparse_dimension, UnsafePointer&lt;Float>!, UnsafePointer&lt;sparse_index>!) -> sparse_status

Inserts a list of scalar entries into a single row of a single-precision sparse matrix.

