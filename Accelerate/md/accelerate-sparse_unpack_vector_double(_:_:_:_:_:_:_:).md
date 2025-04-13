

- Accelerate
-  sparse_unpack_vector_double(\_:\_:\_:\_:\_:\_:\_:) 

Function

# sparse_unpack_vector_double(\_:\_:\_:\_:\_:\_:\_:)

Extracts elements from the sparse vector *x* into the corresponding location in the dense vector *y*, with both vectors containing double-precision values.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 3.0+

``` source
func sparse_unpack_vector_double(
    _ N: sparse_dimension,
    _ nz: sparse_dimension,
    _ zero: Bool,
    _ x: UnsafePointer!,
    _ indx: UnsafePointer!,
    _ y: UnsafeMutablePointer!,
    _ incy: sparse_stride
)
```

## Parameters 

`N`  

The number of elements in the dense vector *y*.

`nz`  

The number of nonzero entries in the sparse vector *x*.

`zero`  

When true, zero the elements of *y* which do not have nonzero values written to them. When false ignore the elements of *y* which do not have nonzero values written to them.

`x`  

Pointer to the dense storage for the values of the sparse vector *x*. The corresponding entry in `indx` holds the index of the value. Contains `nz` values.

`indx`  

Pointer to the dense storage for the index values of the sparse vector *x*. The corresponding entry in *x* holds the values of the vector. Contains `nz` values.

Indices are always assumed to be stored in ascending order. Additionally, indices are assumed to be unique. Undefined behavior if either of these assumptions are not met.All indices are 0 based (the first element of a pointer is `ptr[0]`).

`y`  

Pointer to the dense vector y. Expected to be of size `N * abs(incy)` elements. Negative strides are supported. Note, unlike dense BLAS routines, the pointer points to the last element when stride is negative. On exit, the entries described by the indices in `indx` will be filled with the corresponding values in `x` and all other values will be unchanged if parameter zero is false, or set to zero if parameter zero is true.

`incy`  

Increment between valid values in the dense vector y. Negative strides are supported.

## Discussion

This function extracts elements from the sparse vector *x* into the corresponding location in the dense vector *y*. It can optionally zero the unused values of *y* by setting the `zero` parameter to true.

The function is equivalent to the following code.

```
if (zero) 
    for (i in 0 .. N-1) 
        y[i*incy] = 0;
for (i in 0 .. nz-1) 
    if (indx[i] 

On exit, *y* has been updated with the nonzero values. If `nz` is less than or equal to zero, *y* is unchanged.

Important

Apple provides the BLAS and LAPACK libraries under the Accelerate framework to be in line with LAPACK 3.9.1. Starting with iOS 18, iPadOS 18, macOS 15, tvOS 18, watchOS 18, and visionOS 2, the libraries are in line with LAPACK 3.11.0. These new interfaces provide additional functionality, as well as a new ILP64 interface. To use the new interfaces, define `ACCELERATE_NEW_LAPACK` before including the Accelerate or vecLib headers. For ILP64 interfaces, also define `ACCELERATE_LAPACK_ILP64`. For Swift projects, specify `ACCELERATE_NEW_LAPACK=1` and `ACCELERATE_LAPACK_ILP64=1` as preprocessor macros in Xcode build settings.

## See Also

### Sparse Utility Operations

func sparse_get_vector_nonzero_count_double(sparse_dimension, UnsafePointer&lt;Double>!, sparse_stride) -> Int

Returns the number of nonzero values in the double-precision dense vector *x*.

func sparse_get_vector_nonzero_count_float(sparse_dimension, UnsafePointer&lt;Float>!, sparse_stride) -> Int

Returns the number of nonzero values in the single-precision dense vector *x*.

func sparse_pack_vector_double(sparse_dimension, sparse_dimension, UnsafePointer&lt;Double>!, sparse_stride, UnsafeMutablePointer&lt;Double>!, UnsafeMutablePointer&lt;sparse_index>!) -> Int

Packs nonzero values from a double-precision dense vector to a destination array.

func sparse_pack_vector_float(sparse_dimension, sparse_dimension, UnsafePointer&lt;Float>!, sparse_stride, UnsafeMutablePointer&lt;Float>!, UnsafeMutablePointer&lt;sparse_index>!) -> Int

Packs nonzero values from a single-precision dense vector to a destination array.

func sparse_unpack_vector_float(sparse_dimension, sparse_dimension, Bool, UnsafePointer&lt;Float>!, UnsafePointer&lt;sparse_index>!, UnsafeMutablePointer&lt;Float>!, sparse_stride)

Extracts elements from the sparse vector *x* into the corresponding location in the dense vector *y*, with both vectors containing single-precision values.

