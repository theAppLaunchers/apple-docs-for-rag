

- Accelerate
- vImage_YpCbCrPixelRange
-  init(Yp_bias:CbCr_bias:YpRangeMax:CbCrRangeMax:YpMax:YpMin:CbCrMax:CbCrMin:) 

Initializer

# init(Yp_bias:CbCr_bias:YpRangeMax:CbCrRangeMax:YpMax:YpMin:CbCrMax:CbCrMin:)

Returns a structure describing range and clamping information for Y’CbCr pixel formats.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
init(
    Yp_bias: Int32,
    CbCr_bias: Int32,
    YpRangeMax: Int32,
    CbCrRangeMax: Int32,
    YpMax: Int32,
    YpMin: Int32,
    CbCrMax: Int32,
    CbCrMin: Int32
)
```

## Parameters 

`Yp_bias`  

The encoding for `Y' = 0.0` for this video format (varies by bit depth).

`CbCr_bias`  

The encoding for `{Cb, Cr} = 0.0` for this video format. This is usually the middle of the range of CbCr, not the low end.

`YpRangeMax`  

The encoding for `Y' = 1.0` for this video format. For video range, this is typically less than the maximum representable value.

`CbCrRangeMax`  

The encoding for `{Cb, Cr} = 0.5` for this video format. This is usually near the high end of the encodable range (e.g. `0xf0`), if not the maximum encodable value (e.g. `0xff`).

`YpMax`  

The encoding for the maximum allowed Y’ value. All values larger than this will be clamped to this value.

`YpMin`  

The encoding of the minimum allowed Y’ value. All values less than this will be clamped to this value.

`CbCrMax`  

The encoding of the maximum allowed `{Cb, Cr}` value. All chroma values greater than this value will be clamped to this value.

`CbCrMin`  

The encoding of the minimum allowed `{Cb, Cr}` value. All chroma values less than this value will be clamped to this value.

## Return Value

A structure describing range and clamping information for Y’CbCr pixel formats.

## See Also

### Creating a Pixel Range

init()

