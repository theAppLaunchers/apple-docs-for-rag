

- Metal
- HDR Content
-  Implementing Tone Mapping on Reference Displays 

Article

# Implementing Tone Mapping on Reference Displays

Detect reference displays and keep your content within the capabilities of the display hardware.

## Overview

Reference displays are calibrated to produce accurate brightness and color values within a specified range, which you use in a controlled environment to create optimized video content. Always establish if you’re using a reference display before you process any data so you can avoid system tone mapping and clamp pixel values to the range the display can accurately produce.

To determine if you’re using a reference display, read the screen’s maximumReferenceExtendedDynamicRangeColorComponentValue property. If the display is a reference display, the value of this property is a nonzero value that represents the largest possible pixel value the display can reproduce without clamping or tone mapping. This value may be less than maximumExtendedDynamicRangeColorComponentValue.

To guarantee the reference display presents your content accurately, perform your own tone mapping in a linear color space and keep pixel values between `0.0` and the reference maximum. For more information, see Performing Your Own Tone Mapping.

## See Also

### High Dynamic Range Content

Processing HDR Images with Metal

Implement a post-processing pipeline using the latest features on Apple GPUs.

Displaying HDR Content in a Metal Layer

Bring your high dynamic range (HDR) content to compatible Mac displays.

Determining Support for EDR Values

Check whether a display supports EDR.

Using Color Spaces to Display HDR Content

Use a color space when you don’t need to edit or process the pixel data.

Using System Tone Mapping on Video Content

Use EDR metadata to apply the default system tone mapping to a layer.

Performing Your Own Tone Mapping

Apply your own tone mapping to get the exact behavior you want.

