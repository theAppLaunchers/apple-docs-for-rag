

- Swift
- Array
-  monoscopicForVideoOutput() 

Type Method

# monoscopicForVideoOutput()

Creates a collection of CMTags with the required tags to describe monoscopic video, where there is no stereo view, e.g. kCMTagStereoNone.

iOS 17.2+iPadOS 17.2+Mac Catalyst 17.2+macOS 14.2+tvOS 17.2+visionOS 1.1+watchOS 10.2+

``` source
static func monoscopicForVideoOutput() -> [CMTag]
```

Available when `Element` is `CMTag`.

