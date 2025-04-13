

- AVFoundation
- AVAssetVariantQualifier
-  predicate(forPresentationWidth:operatorType:) 

Type Method

# predicate(forPresentationWidth:operatorType:)

Creates a predicate with a width and operator type.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 10.0+

``` source
class func predicate(
    forPresentationWidth width: CGFloat,
    operatorType: NSComparisonPredicate.Operator
) -> NSPredicate
```

## Parameters 

`width`  

The presentation width.

`operatorType`  

The predicate’s operator type.

## Return Value

A predicate object that you use to to create an AVAssetVariantQualifier.

## See Also

### Creating a Variant Qualifier

convenience init(variant: AVAssetVariant)

Creates a variant qualifier with an asset variant.

class AVAssetVariant

An object that represents a bit rate variant.

convenience init(predicate: NSPredicate)

Creates a variant qualifier with a predicate.

class func predicate(forChannelCount: Int, mediaSelectionOption: AVMediaSelectionOption, operatorType: NSComparisonPredicate.Operator) -> NSPredicate

Creates a predicate with a channel count, media selection option, and operator type.

class func predicate(forPresentationHeight: CGFloat, operatorType: NSComparisonPredicate.Operator) -> NSPredicate

Creates a predicate with a height and operator type.

class func predicate(forBinauralAudio: Bool, mediaSelectionOption: AVMediaSelectionOption) -> NSPredicate

Creates a predicate for binaural audio.

class func predicate(forDownmixAudio: Bool, mediaSelectionOption: AVMediaSelectionOption) -> NSPredicate

Creates a predicate for downmix audio.

class func predicate(forImmersiveAudio: Bool, mediaSelectionOption: AVMediaSelectionOption) -> NSPredicate

Creates a predicate for immersive audio.

class func predicate(forAudioSampleRate: Double, mediaSelectionOption: AVMediaSelectionOption, operatorType: NSComparisonPredicate.Operator) -> NSPredicate

Creates a predicate for audio sample rate.

