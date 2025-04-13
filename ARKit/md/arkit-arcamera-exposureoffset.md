

- ARKit
- ARCamera
-  exposureOffset 

Instance Property

# exposureOffset

A value you supply to your custom renderer to light your scene.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+

``` source
var exposureOffset: Float { get }
```

## Discussion

If your app displays an AR experience using a custom Metal renderer, use this value to light your scene during its post-processed lighting stage.

Lighting a scene using exposureOffset is normally more performant than scaling each light source in your scene based on the value of the frame’s lightEstimate.

