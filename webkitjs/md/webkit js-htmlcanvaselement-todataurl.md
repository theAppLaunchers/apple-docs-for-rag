

- WebKit JS
- HTMLCanvasElement
-  toDataURL 

Instance Method

# toDataURL

Returns a data URL containing an image of the canvas.

Safari Desktop 4.0+Safari Mobile 3.0+

``` source
DOMString toDataURL(
    optional DOMString? type
);
```

## Parameters 

`type`  

A string containing the MIME type of the data, such as `"image/png"`. This parameter is optional. If omitted, the data URL is formatted as a `.png` file.

`quality`  

A floating point number containing the quality of the JPEG image. This parameter is valid only if the `type` parameter is set to `"image/jpeg"`. This parameter must be in the range of 0 to 1, inclusive. This parameter is optional. If omitted, the default quality of 1 is used (highest quality).

## Return Value

Returns a data URL containing image data of a snapshot of the canvas. The image data is in `.png` format unless otherwise specified.

## Discussion

Use this method to record an image of the canvas’ contents as `.png` or `.jpg` file. The method returns the image as a data URL. The image can be drawn back to the canvas later using the drawing context’s `drawImage` method.

### Special Considerations

The HTML5 specification currently requires `toDataURL()` to support the `.png` format. Safari also supports the `image/jpeg` type, but other HTML5-savvy browsers may not.

