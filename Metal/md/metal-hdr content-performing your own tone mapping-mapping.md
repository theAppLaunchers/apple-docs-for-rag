

- Metal
- HDR Content
-  Performing Your Own Tone Mapping 

Article

# Performing Your Own Tone Mapping

Apply your own tone mapping to get the exact behavior you want.

## Overview

To perform your own EDR tone mapping, create a Metal layer, give it an extended linear color space, and set its wantsExtendedDynamicRangeContent property to true. For example, the code below creates a Metal layer with an extended color space that linearly maps pixel values to luminance values:

```
CAMetalLayer *metalLayer = [CAMetalLayer new];
metalLayer.wantsExtendedDynamicRangeContent = YES;
metalLayer.pixelFormat = MTLPixelFormatRGBA16Float;
const CFStringRef name = kCGColorSpaceExtendedLinearSRGB;
CGColorSpaceRef colorspace = CGColorSpaceCreateWithName(name);
metalLayer.colorspace = colorspace;
CGColorSpaceRelease(colorspace);
```

### Understand EDR Pixel Values

On Macs that support EDR, a `1.0` value for a pixel corresponds to the maximum standard dynamic range (SDR) brightness level, but this brightness level doesn’t have to correspond to the maximum brightness of the display. If the display can produce higher brightness levels, additional range (headroom) may be available. The amount of headroom may vary, depending on the actual display characteristics:

- If the UI brightness level is at `100` nits and the panel is capable of a maximum brightness of `400` nits, then enabling EDR allows values up to `4.0` to be displayed at `400` nits.

- On the same panel, if the user adjusts the UI brightness level to `200` nits, then 1.0 values are displayed at `200` nits, and `2.0` values are at `400` nits.

### Map Your Content to the Available Range

The actual upper bound on displayable values may vary from moment to moment. To determine the current upper bound, read the NSScreen object’s maximumExtendedDynamicRangeColorComponentValue property. Note that even on a display that supports EDR, the current maximum might be 1.0, if the display is set to the maximum possible brightness.

The following code reads the maximumExtendedDynamicRangeColorComponentValue property as part of the work it does to process a frame. When rendering the frame, map all values to be between `0` and the current maximum value. If you specify values above this value, the system clamps the value to be no higher than the current maximum value.

```
id drawable = metalLayer.nextDrawable;
NSScreen *screen = view.window.screen;
float maxEDR = screen.maximumExtendedDynamicRangeColorComponentValue;
// 

Register for the didChangeScreenParametersNotification notification to be informed when the current maximum value changes for a display. Also, note that a user may move the content to a different display.

If you have content that exceeds the current capabilities of the display, decide how you want to present that to the user. For example, you might tone map the content into the available range (adapting the content each time you render a frame), or you might notify the user that some of the content is beyond the capability of the display. When users increase the brightness, they typically expect midtones to increase and highlights to be compressed to fit into the range of the display.

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

Implementing Tone Mapping on Reference Displays

Detect reference displays and keep your content within the capabilities of the display hardware.

