

- AVFoundation
- AVCaptionRenderer
-  render(in:for:) 

Instance Method

# render(in:for:)

Draw the captions for the time you specify.

iOS 18.0+iPadOS 18.0+Mac Catalyst 15.0+macOS 12.0+

``` source
func render(
    in ctx: CGContext,
    for time: CMTime
)
```

## Parameters 

`ctx`  

The drawing content.

`time`  

The time value for which the system draws the captions.

