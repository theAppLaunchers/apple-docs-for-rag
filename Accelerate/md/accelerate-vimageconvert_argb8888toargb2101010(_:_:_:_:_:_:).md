

- Accelerate
-  vImageConvert_ARGB8888ToARGB2101010(\_:\_:\_:\_:\_:\_:) 

Function

# vImageConvert_ARGB8888ToARGB2101010(\_:\_:\_:\_:\_:\_:)

Converts an 8-bit-per-channel, 4-channel interleaved buffer to an ARGB2101010 32-bit, 4-channel buffer with permutation.

iOS 9.3+iPadOS 9.3+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
func vImageConvert_ARGB8888ToARGB2101010(
    _ src: UnsafePointer,
    _ dest: UnsafePointer,
    _ RGB101010RangeMin: Int32,
    _ RGB101010RangeMax: Int32,
    _ permuteMap: UnsafePointer!,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`src`  

The source vImage buffer.

`dest`  

A pointer to the destination vImage buffer structure. You’re responsible for filling out the height, width, and rowBytes fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

`RGB101010RangeMin`  

The minimum pixel value for the destination image.

`RGB101010RangeMax`  

The maximum pixel value for the destination image.

`permuteMap`  

An array of four 8-bit integers with the values `0`, `1`, `2`, and 3, in some order. Each value specifies the channel from the source image that the function copies to the destination channel at the corresponding index.

`flags`  

The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## Discussion

The function uses the following calculation to perform the conversion:

```
 uint32_t *srcPixel = src.data;
 srcPixel += 1;

 int32_t R10 = (pixel >> 20) & 0x3ff;
 int32_t G10 = (pixel >> 10) & 0x3ff;
 int32_t B10 = (pixel >>  0) & 0x3ff;
 int32_t range10 = RGB101010RangeMax - RGB101010RangeMin;

 int16_t R16, G16, B16;
 R16 = ((R10 - RGB101010RangeMin) * 4096 + (range10 >> 1)) / range10;
 G16 = ((G10 - RGB101010RangeMin) * 4096 + (range10 >> 1)) / range10;
 B16 = ((B10 - RGB101010RangeMin) * 4096 + (range10 >> 1)) / range10;

 R16 = CLAMP(INT16_MIN, R16, INT16_MAX);
 G16 = CLAMP(INT16_MIN, G16, INT16_MAX);
 B16 = CLAMP(INT16_MIN, B16, INT16_MAX);

 int16_t ARGB[4];
 ARGB[0] = alpha;
 ARGB[1] = R16;
 ARGB[2] = G16;
 ARGB[3] = B16;

 int16_t *destPixel = dest.data;
 destPixel[0] = ARGB[permuteMap[0]];
 destPixel[1] = ARGB[permuteMap[1]];
 destPixel[2] = ARGB[permuteMap[2]];
 destPixel[3] = ARGB[permuteMap[3]];
 destPixel += 4;

```

## See Also

### Converting from 8-bit buffers

func vImageConvert_ARGB8888ToRGBA1010102(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, Int32, Int32, UnsafePointer&lt;UInt8>!, vImage_Flags) -> vImage_Error

Converts an 8-bit-per-channel, 4-channel interleaved buffer to an RGBA1010102 32-bit, 4-channel buffer with permutation.

func vImageConvert_ARGB8888ToXRGB2101010(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, Int32, Int32, UnsafePointer&lt;UInt8>!, vImage_Flags) -> vImage_Error

Converts an 8-bit-per-channel, 4-channel interleaved buffer to an ARGB2101010 32-bit, 4-channel buffer with permutation.

