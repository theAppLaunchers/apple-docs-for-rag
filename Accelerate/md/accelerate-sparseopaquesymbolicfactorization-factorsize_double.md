

- Accelerate
- SparseOpaqueSymbolicFactorization
-  factorSize_Double 

Instance Property

# factorSize_Double

Minimum size, in bytes, required to store numerical factors in doubles.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var factorSize_Double: Int
```

## Discussion

If numerical pivoting requires a pivot to be delayed, the actual size required may be larger.

## See Also

### Inspecting a Factorization’s Structure

var attributes: SparseAttributes_t

The attributes of the factorization.

struct SparseAttributes_t

A structure that represents the attributes of a matrix.

var blockSize: UInt8

The block size.

var columnCount: Int32

The number of columns.

var rowCount: Int32

The number of rows.

var workspaceSize_Double: Int

Size, in bytes, of workspace required to perform numerical factorization in doubles.

var workspaceSize_Float: Int

Size, in bytes, of workspace required to perform numerical factorization in floats.

var factorSize_Float: Int

Minimum size, in bytes, required to store numerical factors in float.

