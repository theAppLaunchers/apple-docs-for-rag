

- Video Toolbox
- VTMotionBlurConfiguration
-  init(frameWidth:frameHeight:usePrecomputedFlow:qualityPrioritization:revision:) 

Initializer

# init(frameWidth:frameHeight:usePrecomputedFlow:qualityPrioritization:revision:)

Creates a new motion blur configuration with specified flow width and height.

macOS 15.4+

``` source
init?(
    frameWidth: Int,
    frameHeight: Int,
    usePrecomputedFlow: Bool,
    qualityPrioritization: VTMotionBlurConfiguration.QualityPrioritization,
    revision: VTMotionBlurConfiguration.Revision
)
```

## Parameters 

`frameWidth`  

The width of the source frame in pixels. Maximum value is 8192 pixels for macOS, and 4096 pixels for iOS.

`frameHeight`  

The height of the source frame in pixels. Maximum value is 4320 pixels for macOS, and 2160 pixels for iOS.

`usePrecomputedFlow`  

If true it indicates that the optical flow will be provided by the user, if false this configuration will compute the optical flow on the fly.

`qualityPrioritization`  

Instance to control quality and performance levels. See VEMotionBlurConfigurationQualityPrioritization for more information.

`revision`  

The specific algorithm or configuration revision that is to be used to perform the request.

## Discussion

Initialization fails if the dimensions are out of range or revision is unsupported.

