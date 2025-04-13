

- Accelerate
-  vImageConvert_ARGBToYpCbCr_GenerateConversion(\_:\_:\_:\_:\_:\_:) 

Function

# vImageConvert_ARGBToYpCbCr_GenerateConversion(\_:\_:\_:\_:\_:\_:)

Generates the information that describes the conversion from ARGB to YpCbCr.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 8.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageConvert_ARGBToYpCbCr_GenerateConversion(
    _ matrix: UnsafePointer,
    _ pixelRange: UnsafePointer,
    _ outInfo: UnsafeMutablePointer,
    _ inARGBType: vImageARGBType,
    _ outYpCbCrType: vImageYpCbCrType,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`matrix`  

A pointer to vImage_ARGBToYpCbCrMatrix that contains the matrix coefficients for the conversion.

`pixelRange`  

A pointer to vImage_YpCbCrPixelRange that contains the pixel range information for the conversion.

`outInfo`  

A pointer to vImage_ARGBToYpCbCr that’s initialized with information for the conversion function to use later.

`inARGBType`  

A vImageARGBType to specify the input (ARGB) format.

`outYpCbCrType`  

A vImageYpCbCrType to specify the output (YpCbCr) format.

`flags`  

The options to use when performing this operation. Set the kvImagePrintDiagnosticsToConsole flag to print debug messages when a problem occurs.

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## Discussion

You use this function to create the vImage_ARGBToYpCbCr conversion information necessary for all RGB-to-YUV conversion functions.

The following example shows how to prepare for the conversion of ARGB8888 to a YUV format with ITU 601 video range:

```
 vImage_Error err = kvImageNoError;
 vImage_Flags flags = kvImageNoFlags;
 vImage_YpCbCrPixelRange pixelRange;
 vImage_ARGBToYpCbCr outInfo;

 pixelRange.Yp_bias         =   16;     // encoding for Y' = 0.0
 pixelRange.CbCr_bias       =  128;     // encoding for CbCr = 0.0
 pixelRange.YpRangeMax      =  235;     // encoding for Y'= 1.0
 pixelRange.CbCrRangeMax    =  240;     // encoding for CbCr = 0.5
 pixelRange.YpMax           =  255;     // a clamping limit above which the value is not allowed to go. 255 is fastest. Use pixelRange.YpRangeMax if you don't want Y' > 1.
 pixelRange.YpMin           =    0;     // a clamping limit below which the value is not allowed to go. 0 is fastest. Use pixelRange.Yp_bias if you don't want Y'  0.5
 pixelRange.CbCrMin         =    0;     // a clamping limit above which the value is not allowed to go. 0 is fastest.  Use (2*pixelRange.CbCr_bias - pixelRange.CbCrRangeMax), if you don't want CbCr 

The following example shows how you might define your own conversion coefficients:

```
 vImage_ARGBToYpCbCrMatrix matrix;;
 vImage_YpCbCrPixelRange pixelRange;

 matrix.R_Yp          =  0.2989f;
 matrix.G_Yp          =  0.5866f;
 matrix.B_Yp          =  0.1144f;
 matrix.R_Cb          = -0.1688f;
 matrix.G_Cb          = -0.3312f;
 matrix.B_Cb_R_Cr     =  0.5f;
 matrix.G_Cr          = -0.4183f;
 matrix.B_Cr          = -0.0816f;
 pixelRange.Yp_bias         =   16;     // encoding for Y' = 0.0
 pixelRange.CbCr_bias       =  128;     // encoding for CbCr = 0.0
 pixelRange.YpRangeMax      =  235;     // encoding for Y'= 1.0
 pixelRange.CbCrRangeMax    =  240;     // encoding for CbCr = 0.5
 pixelRange.YpMax           =  255;     // a clamping limit above which the value is not allowed to go. 255 is fastest. Use pixelRange.YpRangeMax if you don't want Y' > 1.
 pixelRange.YpMin           =    0;     // a clamping limit below which the value is not allowed to go. 0 is fastest. Use pixelRange.Yp_bias if you don't want Y'  0.5
 pixelRange.CbCrMin         =    0;     // a clamping limit above which the value is not allowed to go. 0 is fastest.  Use (2*pixelRange.CbCr_bias - pixelRange.CbCrRangeMax), if you don't want CbCr 

The vImage_ARGBToYpCbCr structure this function creates can be reused concurrently, multiple times from multiple threads.

The conversions that are available are:

|       | RGB8 | RGB16Q12 | RGB16 |
|-------|------|----------|-------|
| YUV8  | Y    | N        | N     |
| YUV10 | Y    | Y        | N     |
| YUV12 | Y    | Y        | N     |
| YUV14 | Y    | N        | Y     |
| YUV16 | Y    | N        | Y     |

## See Also

### Generating conversion information

struct vImageYpCbCrType

Constants that describe the encoding of a YpCbCr image for conversions between RGB and YpCbCr.

struct vImageARGBType

Constants that describe the encoding of an ARGB image for conversions between RGB and YpCbCr.

struct vImage_ARGBToYpCbCrMatrix

The 3 x 3 matrix that the vImage library uses to convert from RGB to YpCbCr.

struct vImage_ARGBToYpCbCr

The information that describes the conversion from ARGB to YpCbCr.

struct vImage_YpCbCrPixelRange

The description of range and clamping information for YpCbCr pixel formats.

