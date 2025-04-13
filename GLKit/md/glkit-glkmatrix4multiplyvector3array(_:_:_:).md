

- GLKit
-  GLKMatrix4MultiplyVector3Array(\_:\_:\_:) 

Function

# GLKMatrix4MultiplyVector3Array(\_:\_:\_:)

Multiplies a `4x4` matrix by an array of `3`-component vectors.

iOS 5.0+iPadOS 5.0+macOS 10.8+tvOS 9.0+

``` source
func GLKMatrix4MultiplyVector3Array(
    _ matrix: GLKMatrix4,
    _ vectors: UnsafeMutablePointer,
    _ vectorCount: Int
)
```

## Parameters 

`matrix`  

The matrix multiplicand.

`vectors`  

On entry, an array of input vectors. On return, an array of output vectors.

`vectorCount`  

The number of vectors in the array.

## Discussion

The input vectors are treated as they were 4-component vectors with a `w`-component of `0.0`.

## See Also

### Performing Mathematical Operations on Vectors

func GLKMatrix4MultiplyVector3(GLKMatrix4, GLKVector3) -> GLKVector3

Multiplies a `4x4` matrix by a `3`-component vector.

func GLKMatrix4MultiplyVector3WithTranslation(GLKMatrix4, GLKVector3) -> GLKVector3

Multiplies a `4x4` matrix by a `3`-component vector, applying translation.

func GLKMatrix4MultiplyVector3ArrayWithTranslation(GLKMatrix4, UnsafeMutablePointer&lt;GLKVector3>, Int)

Multiplies a `4x4` matrix by an array of `3`-component vectors, applying translation.

func GLKMatrix4MultiplyVector4(GLKMatrix4, GLKVector4) -> GLKVector4

Multiplies a `4x4` matrix by a `4`-component vector.

func GLKMatrix4MultiplyVector4Array(GLKMatrix4, UnsafeMutablePointer&lt;GLKVector4>, Int)

Multiplies a `4x4` matrix by an array of `4`-component vectors.

func GLKMatrix4MultiplyAndProjectVector3(GLKMatrix4, GLKVector3) -> GLKVector3

Multiplies a `4x4` matrix by a position vector to create a vector in homogenous coordinates, then projects the result to a `3`-component vector.

func GLKMatrix4MultiplyAndProjectVector3Array(GLKMatrix4, UnsafeMutablePointer&lt;GLKVector3>, Int)

Multiplies a `4x4` matrix by an array of `3`-component vectors. Each result is projected back to `3`-component vector.

