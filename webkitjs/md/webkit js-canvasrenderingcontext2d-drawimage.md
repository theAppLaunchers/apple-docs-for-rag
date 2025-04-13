

- WebKit JS
- CanvasRenderingContext2D
-  drawImage 

Instance Method

# drawImage

Draws the specified image with its upper-left corner at the specified point on the canvas, optionally scaling the image to a specified width and height. Alternatively, draws a specified region of the image, mapped to a specified region of the canvas.

Safari Desktop 3.0+Safari Mobile 1.0+

``` source
void drawImage(
    CanvasImageSource image, 
    unrestricted float x, 
    unrestricted float y
);
```

## Parameters 

`image`  

An image object (an `img`, `canvas`, or `video` element).

`x`  

The x-coordinate of the left edge of the destination for the drawing, in pixels from the left edge of the canvas coordinate system.

`y`  

The y-coordinate of the top of the destination for the drawing, in pixels from the top of the canvas coordinate system.

`ow`  

The width of the drawn image. This parameter is optional; if omitted, the native width of the image is used. If present, the image is scaled to this width.

`oh`  

The height of the drawn image. This parameter is dependent on the `ow` parameter—if `ow` is supplied, `oh` must also be supplied; if `ow` is omitted, `oh` must be omitted. If omitted, the native height of the image is used. If present, the image is scaled to this height.

`sx`  

The x-coordinate of the left edge of the region of the image to draw, in pixels from the left edge of the image.

`sy`  

The y-coordinate of the top of the region of the image to draw, in pixels from the top of the image.

`sw`  

The width of the region of the image to draw.

`sh`  

The height of the region of the image to draw.

`dx`  

The x-coordinate of the left edge of the region of the canvas where the image is to be drawn, in pixels from the left edge of the canvas coordinate system.

`dy`  

The y-coordinate of the top of the region of the canvas where the image is to be drawn, in pixels from the top of the canvas coordinate system.

`dw`  

The width of the drawn image. The specified region of the image is scaled to this width.

`dh`  

The height of the drawn image. The specified region of the image is scaled to this height.

## Discussion

The image object can be an `img` element, a `canvas` element, or a `video` element. Use of the `video` element is not supported in Safari on iOS, however.

If you supply only the image and the x and y coordinates, the image is drawn at its native size at the specified x,y coordinates.

If you supply a width and height, in addition to the image and x,y coordinates, the image is scaled to the specified width and height when it is drawn.

If you specify the image, a source x and y, a source width and height, a destination x and y, and a destination width and height, the specified region of the image is drawn at the specified x,y coordinates on the canvas, scaled to the specified destination width and height.

All drawing is subject to the current clipping region.

All destination parameter values are in the canvas’s current coordinate system, subject to the current transformation matrix (rotation, scale, and so on). Source parameter values (`sx`, `sy`, `sw`, and `sh`) are in CSS pixels, and are not affected by the transformation matrix.

