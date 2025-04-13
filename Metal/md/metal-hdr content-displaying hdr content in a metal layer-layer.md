

- Metal
- HDR Content
-  Displaying HDR Content in a Metal Layer 

Article

# Displaying HDR Content in a Metal Layer

Bring your high dynamic range (HDR) content to compatible Mac displays.

## Overview

In graphics content, *dynamic range* refers to the range of light intensities that a device is capable of displaying or recording, or the range of intensities recorded in a piece of media. Any Mac can display standard dynamic range (SDR) content. Color values are implicitly display-referred, meaning that the brightness value of the content is adapted to the current brightness of the display. When the user adjusts the brightness of their Mac’s display, the SDR content is adjusted directly and proportionally.

### High Dynamic Range

High dynamic range (HDR) content has a wider range of brightness levels than older displays can provide. While HDR doesn’t have a precise definition, many media standards, such as HDR10, define exactly how encoded values correspond to physical brightness levels. In macOS, you can play some forms of HDR video content using AVFoundation APIs like AVPlayerLayer or AVSampleBufferDisplayLayer. Those APIs handle all color management and tone mapping required to display HDR content, even on SDR displays. However, you can also render your own HDR content to a CAMetalLayer. You might do this to support a wider range of brightness levels in a game, or if you are using Metal to process video content.

### Extended Dynamic Range

Some Macs can process pixel data with a wider range of pixel values and send those extended values to the display. In macOS, the ability to process larger pixel values and display them is referred to as extended dynamic range (EDR). When you configure a Metal layer to support extended values, you can provide pixel values — and therefore brightness levels — that exceed the normal SDR range in order to display HDR content.

EDR works similarly to SDR; content is still display-referred, and brightness levels change when the user adjusts the display brightness. If you specify values in the standard range, they are displayed exactly as before. However, whenever the display is capable of displaying brighter pixels, you can provide larger values to present brighter colors. The range of permitted values isn’t fixed; it adapts to the capabilities of the display and its current brightness setting. For example, when the user lowers the display’s brightness setting, the display can still generate brighter values, so the permitted range of values usually increases. (If the user sets a very low brightness, the maximum brightness may be restricted relative to this brightness.)

Some displays, such as the Pro Display XDR, are always capable of displaying brighter pixels than those on an SDR display, and the extended dynamic range is always larger than the standard dynamic range. On displays that don’t support these high brightness levels, or if the user sets the display to its maximum brightness level, the extended range may be the same as the standard dynamic range.

### Reference Displays

The Pro Display XDR is capable of acting as a reference display for HDR authoring. Within a certain range of values, reference displays guarantee very precise color and brightness matching. Users rely on these accurate measurements when creating HDR content for distribution. If your app provides an authoring experience, you can find out whether a display is a reference display and tailor your app’s behavior to take advantage of it.

### Display Techniques

Because many HDR standards use physical brightness levels and EDR uses relative brightness levels, you need to decide how best to adapt your HDR content to the EDR-capable display environment. In many cases, you can provide your HDR data to macOS and it adapts the data to the EDR-capable display. In other cases, you may want to get information about the display directly. Here are some common options:

- If your video content is already tone-mapped and normalized, leave the content in its original form and use an appropriate color space to apply a transfer function to the pixel data. See Using Color Spaces to Display HDR Content.

- If you’re modifying video content and need tone mapping that’s consistent with playback in AVFoundation and other system playback mechanisms, use a linear color space and tell macOS to apply its tone-mapping algorithm to your content. See Using System Tone Mapping on Video Content.

- If you’re rendering arbitrary content, rendering content for a reference display, or if performance is more important than matching the exact system tone mapping, disable system tone mapping and tone map the content yourself. When you render new video or animation frames, you determine the current range of possible values and map your content to match. See Performing Your Own Tone Mapping and Implementing Tone Mapping on Reference Displays.

## See Also

### High Dynamic Range Content

Processing HDR Images with Metal

Implement a post-processing pipeline using the latest features on Apple GPUs.

Determining Support for EDR Values

Check whether a display supports EDR.

Using Color Spaces to Display HDR Content

Use a color space when you don’t need to edit or process the pixel data.

Using System Tone Mapping on Video Content

Use EDR metadata to apply the default system tone mapping to a layer.

Performing Your Own Tone Mapping

Apply your own tone mapping to get the exact behavior you want.

Implementing Tone Mapping on Reference Displays

Detect reference displays and keep your content within the capabilities of the display hardware.

