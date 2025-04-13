

- GLKit
-  GLKMatrix4GetMatrix3(\_:) 

Function

# GLKMatrix4GetMatrix3(\_:)

Returns the upper-left `3x3` section of a `4x4` matrix.

iOS 5.0+iPadOS 5.0+macOS 10.8+tvOS 9.0+

``` source
func GLKMatrix4GetMatrix3(_ matrix: GLKMatrix4) -> GLKMatrix3
```

## Parameters 

`matrix`  

A `4x4` matrix.

## Return Value

A new `3x3` matrix.

## See Also

### Working With Parts of a Matrix

func GLKMatrix4GetMatrix2(GLKMatrix4) -> GLKMatrix2

Returns the upper-left `2x2` section of a `4x4` matrix.

func GLKMatrix4GetColumn(GLKMatrix4, Int32) -> GLKVector4

Retrieves a column from a `4x4` matrix.

func GLKMatrix4GetRow(GLKMatrix4, Int32) -> GLKVector4

Retrieves a row from a `4x4` matrix.

func GLKMatrix4SetColumn(GLKMatrix4, Int32, GLKVector4) -> GLKMatrix4

Returns a new `4x4` matrix with one column replaced by a new vector.

func GLKMatrix4SetRow(GLKMatrix4, Int32, GLKVector4) -> GLKMatrix4

Returns a new `4x4` matrix with one row replaced by a new vector.

