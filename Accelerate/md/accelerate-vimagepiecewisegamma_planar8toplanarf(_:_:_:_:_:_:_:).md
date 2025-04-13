

- Accelerate
-  vImagePiecewiseGamma_Planar8toPlanarF(\_:\_:\_:\_:\_:\_:\_:) 

Function

# vImagePiecewiseGamma_Planar8toPlanarF(\_:\_:\_:\_:\_:\_:\_:)

Applies a piecewise gamma function to transform an 8-bit planar image to a 32-bit planar image.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 7.0+visionOS 1.0+watchOS 1.0+

``` source
func vImagePiecewiseGamma_Planar8toPlanarF(
    _ src: UnsafePointer,
    _ dest: UnsafePointer,
    _ exponentialCoeffs: UnsafePointer,
    _ gamma: Float,
    _ linearCoeffs: UnsafePointer,
    _ boundary: Pixel_8,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`src`  

The source vImage buffer.

`dest`  

A pointer to the destination vImage buffer structure. You’re responsible for filling out the `height`, `width`, and `rowBytes` fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

`exponentialCoeffs`  

An array of three floating-point coefficients that specify the scale, prebias, and postbias for the gamma curve.

`gamma`  

The power function exponent for calculating gamma correction for the gamma curve.

`linearCoeffs`  

An array of two floating-point coefficients that specify the scale and bias for the linear curve.

`boundary`  

A value that defines the boundary between the linear curve and the gamma curve.

`flags`  

The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## Discussion

The piecewise gamma calculation combines a linear and an exponential (gamma) curve on two regions of the input interval, separated by a specified boundary value. When the input is greater than or equal to the boundary value, the function uses the gamma curve to generate the output; otherwise, the function uses the linear curve.

The following describes the operation with `x` representing the input pixel value:

```
if x 

## See Also

### Applying a piecewise gamma function

Adjusting the brightness and contrast of an image

Use a gamma function to apply a linear or exponential curve.

func vImagePiecewiseGamma_Planar8(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;Float>, Float, UnsafePointer&lt;Float>, Pixel_8, vImage_Flags) -> vImage_Error

Applies a piecewise gamma function to transform an 8-bit planar image.

func vImagePiecewiseGamma_Planar8toPlanar16Q12(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;Float>, Float, UnsafePointer&lt;Float>, Pixel_8, vImage_Flags) -> vImage_Error

Applies a piecewise gamma function to transform an 8-bit planar image to a 16Q12 planar image.

func vImagePiecewiseGamma_Planar16Q12(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;Float>, Float, UnsafePointer&lt;Float>, Pixel_16S, vImage_Flags) -> vImage_Error

Applies a piecewise gamma function to transform a 16Q12 planar image.

func vImagePiecewiseGamma_Planar16Q12toPlanar8(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;Float>, Float, UnsafePointer&lt;Float>, Pixel_16S, vImage_Flags) -> vImage_Error

Applies a piecewise gamma function to transform a 16Q12 planar image to an 8-bit planar image.

func vImagePiecewiseGamma_PlanarF(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;Float>, Float, UnsafePointer&lt;Float>, Float, vImage_Flags) -> vImage_Error

Applies a piecewise gamma function to transform a 32-bit planar image.

func vImagePiecewiseGamma_PlanarFtoPlanar8(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;Float>, Float, UnsafePointer&lt;Float>, Float, vImage_Flags) -> vImage_Error

Applies a piecewise gamma function to transform a 32-bit planar image to an 8-bit planar image.

