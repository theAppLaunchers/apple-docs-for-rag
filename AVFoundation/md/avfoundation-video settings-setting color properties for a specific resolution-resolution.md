

- AVFoundation
- Video settings
-  Setting Color Properties for a Specific Resolution 

Article

# Setting Color Properties for a Specific Resolution

Choose the proper color property keys for the desired color range.

## Overview

After specifying the AVVideoColorPropertiesKey, you must specify a color primary, transfer function, and Y’CbCr matrix.

For HD colorimetry, specify:

- AVVideoColorPrimaries_ITU_R_709_2

- AVVideoTransferFunction_ITU_R_709_2

- AVVideoYCbCrMatrix_ITU_R_709_2

For SD colorimetry, specify:

- AVVideoColorPrimaries_SMPTE_C

- AVVideoTransferFunction_ITU_R_709_2

- AVVideoYCbCrMatrix_ITU_R_601_4

For wide gamut HD colorimetry, specify:

- AVVideoColorPrimaries_P3_D65

- AVVideoTransferFunction_ITU_R_709_2

- AVVideoYCbCrMatrix_ITU_R_709_2

If the source and destination color properties differ, AVFoundation matches the color. You must tag the source.

## See Also

### Color properties

let AVVideoAllowWideColorKey: String

The key for a dictionary that indicates whether the client can process wide color.

let AVVideoColorPrimariesKey: String

The key to identify color primaries in a color properties dictionary.

let AVVideoColorPrimaries_EBU_3213: String

The color primary is in the EBU Tech. 3213 color space.

let AVVideoColorPrimaries_ITU_R_2020: String

The color primary is in the ITU_R BT.2020 color space for ultra high definition television.

let AVVideoColorPrimaries_ITU_R_709_2: String

The color primary is in the ITU_R BT.709 color space.

let AVVideoColorPrimaries_P3_D65: String

The color primary uses the DCI-P3 D65 color space.

let AVVideoColorPrimaries_SMPTE_C: String

The color primary uses the SMPTE C color space.

let AVVideoColorPropertiesKey: String

The key for a dictionary that contains properties specifying video color.

let AVVideoTransferFunctionKey: String

The key to identify the transfer function in a color properties dictionary.

let AVVideoTransferFunction_IEC_sRGB: String

The transfer function for the IEC sRGB color space.

let AVVideoTransferFunction_ITU_R_2100_HLG: String

The transfer function for the ITU_R BT.2100 color space.

let AVVideoTransferFunction_ITU_R_709_2: String

The transfer function for the ITU_R BT.709 color space.

let AVVideoTransferFunction_Linear: String

The transfer function for the linear color space.

let AVVideoTransferFunction_SMPTE_240M_1995: String

The transfer function for the SMPTE 240M color space.

let AVVideoTransferFunction_SMPTE_ST_2084_PQ: String

The transfer function for the SMPTE 2084 color space.

