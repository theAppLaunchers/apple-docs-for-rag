

- Accelerate
-  SparseGetStateSize_Double(\_:\_:\_:\_:\_:) 

Function

# SparseGetStateSize_Double(\_:\_:\_:\_:\_:)

Returns the size in bytes necessary for a call to the double-precision sparse iterate method.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
func SparseGetStateSize_Double(
    _ method: SparseIterativeMethod,
    _ preconditioner: Bool,
    _ m: Int32,
    _ n: Int32,
    _ nrhs: Int32
) -> Int
```

## Parameters 

`method`  

The method to return required state space size for.

`preconditioner`  

Set to `true` if your subsequent calls to `SparseIterate` use a preconditioner.

`m`  

The number of rows in matrix *A*.

`n`  

The number of columns in matrix *A*.

`nrhs`  

The number of columns in matrices *B* and *X*.

## Return Value

The size of the required state space, in bytes.

## See Also

### Functions that Calculate Iterate State Size

func SparseGetStateSize_Float(SparseIterativeMethod, Bool, Int32, Int32, Int32) -> Int

Returns the size in bytes necessary for a call to the single-precision sparse iterate method.

