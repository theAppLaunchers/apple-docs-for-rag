

- ARKit
- ARKit in iOS
-  Displaying an AR Experience with Metal 

Article

# Displaying an AR Experience with Metal

Control rendering of your app’s virtual content on top of a camera feed.

## Overview

ARKit includes view classes for easily displaying AR experiences with SceneKit or SpriteKit. However, if instead you build your own rendering engine using Metal, ARKit also provides all the support necessary to display an AR experience with your custom view.

In any AR experience, the first step is to configure an ARSession object to manage camera capture and motion processing. A session defines and maintains a correspondence between the real-world space the device inhabits and a virtual space where you model AR content. To display your AR experience in a custom view, you’ll need to:

1.  Retrieve video frames and tracking information from the session.

2.  Render those frame images as the backdrop for your view.

3.  Use the tracking information to position and draw AR content atop the camera image.

Note

This article covers code found in Xcode project templates. For complete example code, create a new iOS application with the Augmented Reality template, and choose Metal from the Content Technology popup menu.

### Get Video Frames and Tracking Data from the Session

Create and maintain your own ARSession instance, and run it with a session configuration appropriate for the kind of AR experience you want to support. The session captures video from the camera, tracks the device’s position and orientation in a modeled 3D space, and provides ARFrame objects. Each such object contains both an individual video frame image and position tracking information from the moment that frame was captured.

There are two ways to access ARFrame objects produced by an AR session, depending on whether your app favors a pull or a push design pattern.

If you prefer to control frame timing (the pull design pattern), use the session’s currentFrame property to get the current frame image and tracking information each time you redraw your view’s contents. For example, see the following function that a custom renderer calls as part of its regular update process:

```
func updateGameState() {        
    guard let currentFrame = session.currentFrame else {
        return
    }    
    updateSharedUniforms(frame: currentFrame)
    updateAnchors(frame: currentFrame)
    updateCapturedImageTextures(frame: currentFrame)

    if viewportSizeDidChange {
        viewportSizeDidChange = false

        updateImagePlane(frame: currentFrame)
    }
}
```

Alternatively, if your app design favors a push pattern, implement the session(_:didUpdate:) delegate method, and the session will call it once for each video frame it captures (at 60 frames per second by default).

Upon obtaining a frame, you’ll need to draw the camera image, and update and render any overlay content your AR experience includes.

### Draw the Camera Image

Each ARFrame object’s capturedImage property contains a pixel buffer captured from the device camera. To draw this image as the backdrop for your custom view, you’ll need to create textures from the image content and submit GPU rendering commands that use those textures.

The pixel buffer’s contents are encoded in a biplanar YCbCr (also called YUV) data format; to render the image you’ll need to convert this pixel data to a drawable RGB format. For rendering with Metal, you can perform this conversion most efficiently in GPU shader code. Use CVMetalTextureCache APIs to create two Metal textures from the pixel buffer—one each for the buffer’s luma (Y) and chroma (CbCr) planes:

```
func updateCapturedImageTextures(frame: ARFrame) {
    // Create two textures (Y and CbCr) from the provided frame's captured image.
    let pixelBuffer = frame.capturedImage
    if (CVPixelBufferGetPlaneCount(pixelBuffer)  MTLTexture? {
    var mtlTexture: MTLTexture? = nil
    let width = CVPixelBufferGetWidthOfPlane(pixelBuffer, planeIndex)
    let height = CVPixelBufferGetHeightOfPlane(pixelBuffer, planeIndex)

    var texture: CVMetalTexture? = nil
    let status = CVMetalTextureCacheCreateTextureFromImage(nil, capturedImageTextureCache, pixelBuffer, nil, pixelFormat, width, height, planeIndex, &texture)
    if status == kCVReturnSuccess {
        mtlTexture = CVMetalTextureGetTexture(texture!)
    }

    return mtlTexture
}
```

Next, encode render commands that draw those two textures using a fragment function that performs YCbCr to RGB conversion with a color transform matrix:

```
fragment float4 capturedImageFragmentShader(ImageColorInOut in [[stage_in]],
                                            texture2d capturedImageTextureY [[ texture(kTextureIndexY) ]],
                                            texture2d capturedImageTextureCbCr [[ texture(kTextureIndexCbCr) ]]) {

    constexpr sampler colorSampler(mip_filter::linear,
                                   mag_filter::linear,
                                   min_filter::linear);

    const float4x4 ycbcrToRGBTransform = float4x4(
        float4(+1.0000f, +1.0000f, +1.0000f, +0.0000f),
        float4(+0.0000f, -0.3441f, +1.7720f, +0.0000f),
        float4(+1.4020f, -0.7141f, +0.0000f, +0.0000f),
        float4(-0.7010f, +0.5291f, -0.8860f, +1.0000f)
    );

    // Sample Y and CbCr textures to get the YCbCr color at the given texture coordinate.
    float4 ycbcr = float4(capturedImageTextureY.sample(colorSampler, in.texCoord).r,
                          capturedImageTextureCbCr.sample(colorSampler, in.texCoord).rg, 1.0);

    // Return the converted RGB color.
    return ycbcrToRGBTransform * ycbcr;
}
```

Note

Use the displayTransform(for:viewportSize:) method to make sure the camera image covers the entire view. For example use of this method, as well as complete Metal pipeline setup code, see the full Xcode template. (Create a new iOS application with the Augmented Reality template, and choose Metal from the Content Technology popup menu.)

### Track and Render Overlay Content

AR experiences typically focus on rendering 3D overlay content so that the content appears to be part of the real world seen in the camera image. To achieve this illusion, use the ARAnchor class to model the position and orientation of your own 3D content relative to real-world space. Anchors provide transforms that you can reference during rendering.

For example, the Xcode template creates an anchor located about 20 cm in front of the device whenever a user taps on the screen:

```
func handleTap(gestureRecognize: UITapGestureRecognizer) {
    // Create an anchor using the camera's current position.
    if let currentFrame = session.currentFrame {

        // Create a transform with a translation of 0.2 meters in front of the camera.
        var translation = matrix_identity_float4x4
        translation.columns.3.z = -0.2
        let transform = simd_mul(currentFrame.camera.transform, translation)

        // Add a new anchor to the session.
        let anchor = ARAnchor(transform: transform)
        session.add(anchor: anchor)
    }
}
```

In your rendering engine, use the transform property of each ARAnchor object to place visual content. The Xcode template uses each of the anchors added to the session in its `handleTap` method to position a simple cube mesh:

```
func updateAnchors(frame: ARFrame) {
    // Update the anchor's uniform buffer with transforms of the current frame's anchors.
    anchorInstanceCount = min(frame.anchors.count, kMaxAnchorInstanceCount)

    var anchorOffset: Int = 0
    if anchorInstanceCount == kMaxAnchorInstanceCount {
        anchorOffset = max(frame.anchors.count - kMaxAnchorInstanceCount, 0)
    }

    for index in 0..

Note

In a more complex AR experience, you can use hit testing or plane detection to find the positions of real-world surfaces. For details, see the planeDetection property and the hitTest(_:types:) method. In both cases, ARKit provides results as ARAnchor objects, so you still use anchor transforms to place visual content.

### Render with Realistic Lighting

When you configure shaders for drawing 3D content in your scene, use the estimated lighting information in each ARFrame object to produce more realistic shading. See the following code that an app’s custom renderer performs while updating its shared uniforms:

```
// Set up the scene's lighting with the ambient intensity, if available.
var ambientIntensity: Float = 1.0
if let lightEstimate = frame.lightEstimate {
    ambientIntensity = Float(lightEstimate.ambientIntensity) / 1000.0
}
let ambientLightColor: vector_float3 = vector3(0.5, 0.5, 0.5)
uniforms.pointee.ambientLightColor = ambientLightColor * ambientIntensity
```

Note

For the complete set of Metal setup and rendering commands that go with this example, see the full Xcode template. (Create a new iOS application with the Augmented Reality template, and choose Metal from the Content Technology popup menu.)

## See Also

### Setup

Choosing Which Camera Feed to Augment

Add visual effects to the user’s environment in an AR experience through the front or rear camera.

Managing Session Life Cycle and Tracking Quality

Keep the user informed on the current session state and recover from interruptions.

class ARSession

The object that manages the major tasks associated with every AR experience, such as motion tracking, camera passthrough, and image analysis.

Configuration Objects

Configure your augmented reality session to detect and track specific types of content.

