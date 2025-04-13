

- QuickTime File Format
- Text sample description
-  Display flags 

Data field

# Display flags

A 32-bit integer containing flags that describe how the text should be drawn.

## Overview

The following flags are defined:

Don’t auto scale  
Controls text scaling. If this flag is set to `1`, the text media handler reflows the text instead of scaling when the track is scaled. This flag’s value is `0x0002`.

Use movie background color  
Controls background color. If this flag is set to `1`, the text media handler ignores the background color field in the text sample description and uses the movie’s background color instead. This flag’s value is `0x0008`.

Scroll in  
Controls text scrolling. If this flag is set to `1`, the text media handler scrolls the text until the last of the text is in view. This flag’s value is `0x0020`.

Scroll out  
Controls text scrolling. If this flag is set to `1`, the text media handler scrolls the text until the last of the text is gone. This flag’s value is `0x0040`.

Horizontal scroll  
Controls text scrolling. If this flag is set to `1`, the text media handler scrolls the text horizontally; otherwise, it scrolls the text vertically. This flag’s value is `0x0080`.

Reverse scroll  
Controls text scrolling. If this flag is set to `1`, the text media handler scrolls down (if scrolling vertically) or backward (if scrolling horizontally; note that horizontal scrolling also depends upon text justification). This flag’s value is `0x0100`.

Continuous scroll  
Controls text scrolling. If this flag is set to `1`, the text media handler displays new samples by scrolling out the old ones. This flag’s value is `0x0200`.

Drop shadow  
Controls drop shadow. If this flag is set to `1`, the text media handler displays the text with a drop shadow. This flag’s value is `0x1000`.

Anti-alias  
Controls anti-aliasing. If this flag is set to `1`, the text media handler uses anti-aliasing when drawing text. This flag’s value is `0x2000`.

Key text  
Controls background color. If this flag is set to `1`, the text media handler does not display the background color, so that the text overlay background tracks. This flag’s value is `0x4000`.

## See Also

### Data fields

Text justification

A 32-bit integer that indicates how the text should be aligned.

Background color

A 48-bit RGB color that specifies the text’s background color.

Default text box

A 64-bit rectangle that specifies an area to receive text (top, left, bottom, right).

Reserved

A 64-bit value.

Font number

A 16-bit value.

Font face

A 16-bit integer that indicates the font’s style.

Reserved

An 8-bit value.

Reserved

A 16-bit value.

Foreground color

A 48-bit RGB color that specifies the text’s foreground color.

Text name

A Pascal string specifying the name of the font to use to display the text.

