

- Kernel
- IOKit Fundamentals
- IODisplayScalerInformation
-  scalerFeatures 

Instance Property

# scalerFeatures

Mask of scaling features.

macOS 10.3+

``` source
IOOptionBits scalerFeatures;
```

## Discussion

The following values are defined.

|  |  |
|----|----|
| `kIOScaleStretchOnly` | If set, the `framebuffer` can only provide stretched scaling with non-square pixels, without borders. |
| `kIOScaleCanUpSamplePixels` | If set, `framebuffer` can scale up from a smaller number of source pixels to a larger native timing (eg. 640x480 pixels on a 1600x1200 timing). |
| `kIOScaleCanDownSamplePixels` | If set, `framebuffer` can scale down from a larger number of source pixels to a smaller native timing (eg. 1600x1200 pixels on a 640x480 timing). |
| `kIOScaleCanScaleInterlaced` | If set, `framebuffer` can scale an interlaced detailed timing. |
| `kIOScaleCanSupportInset` | If set, `framebuffer` can support scaled modes with non-zero `horizontalScaledInset`, `verticalScaledInset` fields. |
| `kIOScaleCanRotate` | If set, `framebuffer` can support some of the flags in the `kIOScaleRotateFlags` mask. |
| `kIOScaleCanBorderInsetOnly` | If set, `framebuffer` can support scaled modes with non-zero `horizontalScaledInset`, `verticalScaledInset` fields, but requires the active pixels to be equal in size to the inset area, that is, can do insets with a border versus scaling an image. |

**Table 1** Defined Masks

