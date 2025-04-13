

- Metal
- MTLRenderCommandEncoder
-  setViewports(\_:) 

Instance Method

# setViewports(\_:)

Configures the render pipeline with multiple viewports that apply transformations and clipping rectangles.

iOS 12.0+iPadOS 12.0+Mac CatalystmacOS 10.13+tvOS 14.5+visionOS

``` source
func setViewports(_ viewports: [MTLViewport])
```

## Parameters 

`viewports`  

An array of MTLViewport instances the command applies to the render pipeline for transformations and clipping.

## Mentioned in 

Rendering to Multiple Viewports in a Draw Command

## Discussion

Use this method to configure multiple active viewports and corresponding scissor rectangles. Multiple viewports give your app the ability to draw into separate areas of an image with a single draw call. You can either set a single scissor rectangle for all viewports with the setScissorRect(_:) method, or set each viewport’s rectangle with the setScissorRects(_:) method.

Important

The number of scissor rectangles you pass to setScissorRects(_:) needs to match the number of viewports you configure with this method.

The maximum number of viewports and scissor rectangles a GPU supports varies by device family. For more information, see MTLGPUFamily and Detecting GPU Features and Metal Software Versions.

The rendering pipeline sends each primitive to a single viewport and its associated scissor rectangle. You can select which viewport each primitive uses in your vertex shader by adding the `[[viewport_array_index]]` attribute to an output value.

The render pipeline linearly maps vertex positions from normalized device coordinates to viewport coordinates by applying a viewport during the rasterization stage. It applies the transform first and then rasterizes the primitive while clipping any fragments outside the scissor rectangle (see setScissorRect(_:)) or the render target’s extents.

The viewport’s originX and originY properties, which default to `0.0`, represent the number of pixels from the top-left corner of the render target. Positive originX values go to the right and positive originY values go downward. The default values for its width and height properties are the render target’s width and height, respectively. The default values for its znear and zfar properties are `0.0` and `1.0`, respectively, which you can flip.

Note

You can change the render pass’s viewport configuration by calling this method again or by calling the setViewport(_:) method.

The setViewport(_:) method is equivalent to calling this method with a single viewport element in the `viewports` array.

## See Also

### Configuring Viewport and Scissor Behavior

func setViewport(MTLViewport)

Configures the render pipeline with a viewport that applies a transformation and a clipping rectangle.

**Required**

func setScissorRect(MTLScissorRect)

Configures a rectangle for the fragment scissor test.

**Required**

func setScissorRects([MTLScissorRect])

Configures multiple rectangles for the fragment scissor test.

