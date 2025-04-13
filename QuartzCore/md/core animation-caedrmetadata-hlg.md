

- Core Animation
- CAEDRMetadata
-  hlg 

Type Property

# hlg

Extended dynamic range (EDR) metadata for the Hybrid Log-Gamma (HLG) transfer function.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 10.15+visionOS 1.0+

``` source
class var hlg: CAEDRMetadata { get }
```

## Discussion

Your content should be scene referred and encoded with the ITU-R BT.2100-2 Hybrid Log Gamma (HLG) opto-electrical transfer function (OETF). The system applies the opto-optical transfer function (OOTF) based on peak display brightness and ambient lighting. If you’re rendering to a CAMetalLayer with a linear colorspace (for floating point EDR layers), you must apply the HLG inverse OETF without normalization, to provide a nominal range of `[0, 12]`.

For more information on HLG, see https://www.itu.int/rec/R-REC-BT.2100.

