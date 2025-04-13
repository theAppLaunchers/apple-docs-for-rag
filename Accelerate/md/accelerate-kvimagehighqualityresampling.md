

- Accelerate
-  kvImageHighQualityResampling 

Global Variable

# kvImageHighQualityResampling

A flag that uses a higher-quality, slower resampling filter for geometry operations.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.3+tvOSvisionOS 1.0+watchOS 2.0+

``` source
var kvImageHighQualityResampling: Int { get }
```

## Mentioned in 

Resampling in vImage

Building a Basic Image-Processing Workflow

Applying geometric transforms to images

## Discussion

vImage uses Lanczos interpolation for resampling.

Lanczos interpolation provides excellent results for geometric operations on images, preserves details, and reduces aliasing artifacts compared to other resampling techniques.

By default, vImage uses the Lanczos-3 algorithm for resampling. Set this flag to switch to the higher-quality Lanczos-5 algorithm.

## See Also

### Constants

struct Options

Set flags on vImage operations to specify processing options.

var kvImageNoFlags: Int

A flag that sets the behavior to the default.

var kvImageLeaveAlphaUnchanged: Int

A flag that restricts the operation to red, green, and blue channels only.

var kvImageDoNotTile: Int

A flag that disables vImage internal tiling routines.

var kvImageGetTempBufferSize: Int

A flag that returns the minimum temporary buffer size for the operation, given the parameters provided.

var kvImagePrintDiagnosticsToConsole: Int

A flag that prints a debug message if the operation fails.

var kvImageNoAllocate: Int

A flag that prevents vImage from allocating additional storage.

var kvImageHDRContent: Int

A flag that uses HDR-aware methods.

var kvImageDoNotClamp: Int

A flag that disables clamping in some conversions to floating-point formats.

var kvImageUseFP16Accumulator: Int

A flag that specifies vImage uses faster but lower-precision internal arithmetic for floating-point 16-bit operations.

