

- Compositor Services
- LayerRenderer
-  minimumFrameRepeatCount 

Instance Property

# minimumFrameRepeatCount

The number of additional frames for which the system displays the same content.

visionOS 1.0+

``` source
var minimumFrameRepeatCount: Int32 { get set }
```

## Discussion

The minimum frame repeat count contains the number of additional frames that display the same content. For example, if this value is `1`, the layer displays the same content for the duration of two screen update cycles.

Use this value to determine the pacing of your drawing operations. A higher repeat count increases the amount of time you have to render each frame, and decreases the amount of power your app uses per frame. However, higher repeat counts also mean your content updates less frequently.

