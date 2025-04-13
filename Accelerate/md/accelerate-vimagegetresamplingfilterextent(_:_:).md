

- Accelerate
-  vImageGetResamplingFilterExtent(\_:\_:) 

Function

# vImageGetResamplingFilterExtent(\_:\_:)

Returns the maximum sampling radius for a resampling filter.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 7.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageGetResamplingFilterExtent(
    _ filter: ResamplingFilter,
    _ flags: vImage_Flags
) -> vImagePixelCount
```

## Parameters 

`filter`  

The resampling filter to query.

`flags`  

The flags you intend to pass to the horizontal or vertical shear function.

## Return Value

The maximum sampling radius for the specified resampling filter.

## Discussion

This function returns the maximum distance from any pixel that the filter will look, either horizontally or vertically, depending on whether a horizontal or vertical shear is used. It’s analogous to `kernelWidth` in vImageNewResamplingFilterForFunctionUsingBuffer(_:_:_:_:_:_:), but might be slightly larger to allow for extra slope when dealing with subpixel coordinates during resampling.

## See Also

### Resampling filters

func vImageNewResamplingFilter(Float, vImage_Flags) -> ResamplingFilter!

Creates a resampling filter object that corresponds to the default kernel supplied by the vImage framework.

func vImageNewResamplingFilterForFunctionUsingBuffer(ResamplingFilter, Float, ((UnsafePointer&lt;Float>?, UnsafeMutablePointer&lt;Float>?, UInt, UnsafeMutableRawPointer?) -> Void)!, Float, UnsafeMutableRawPointer!, vImage_Flags) -> vImage_Error

Creates a resampling filter object that encapsulates a resampling kernel function that you provide.

func vImageGetResamplingFilterSize(Float, ((UnsafePointer&lt;Float>?, UnsafeMutablePointer&lt;Float>?, UInt, UnsafeMutableRawPointer?) -> Void)!, Float, vImage_Flags) -> Int

Returns the minimum size, in bytes, for the buffer needed by the new resampling filter function.

func vImageDestroyResamplingFilter(ResamplingFilter!)

Disposes of a resampling filter object.

