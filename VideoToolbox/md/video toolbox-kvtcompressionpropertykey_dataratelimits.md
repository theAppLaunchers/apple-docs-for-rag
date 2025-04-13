

- Video Toolbox
-  kVTCompressionPropertyKey_DataRateLimits 

Global Variable

# kVTCompressionPropertyKey_DataRateLimits

Zero, one, or two hard limits on data rate.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.8+tvOS 10.2+visionOS 1.0+

``` source
let kVTCompressionPropertyKey_DataRateLimits: CFString
```

## Discussion

Each hard limit is described by a data size in bytes and a duration in seconds, and requires that the total size of compressed data for any contiguous segment of that duration (in decode time) not exceed the data size. By default, no data rate limits are set. The property is a doc://com.apple.documentation/documentation/corefoundation/cfarray-s28 of an even number of doc://com.apple.documentation/documentation/corefoundation/cfnumber-rjd objects, alternating between bytes and seconds. Note that data rate settings only have an effect when timing information is provided for source frames, and that some codecs do not support limiting to specified data rates.

## See Also

### Rate Control

let kVTCompressionPropertyKey_AverageBitRate: CFString

The long-term desired average bit rate in bits per second.

let kVTCompressionPropertyKey_ConstantBitRate: CFString

Requires that the encoder use a Constant Bit Rate algorithm.

let kVTCompressionPropertyKey_EstimatedAverageBytesPerFrame: CFString

An estimate of the expected size in bytes of a single encoded frame based on the current configuration.

let kVTCompressionPropertyKey_MoreFramesAfterEnd: CFString

A Boolean value indicating whether and how a compression session concatenates frames with other compressed frames to form a longer series.

let kVTCompressionPropertyKey_MoreFramesBeforeStart: CFString

A Boolean value that indicates whether and how a compression session concatenates frames with other compressed frames to form a longer series.

let kVTCompressionPropertyKey_Quality: CFString

The desired compression quality.

let kVTCompressionPropertyKey_TargetQualityForAlpha: CFString

The target quality to use for encoding the alpha channel.

