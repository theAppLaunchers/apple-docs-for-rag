

- UIKit
- UIImage
-  topCapHeight Deprecated

Instance Property

# topCapHeight

The vertical end-cap size.

iOSiPadOSMac CatalystvisionOSwatchOS

``` source
var topCapHeight: Int { get }
```

Deprecated

Use the capInsets property instead.

## Discussion

End caps specify the portion of an image that should not be resized when an image is stretched. This technique is used to implement buttons and other resizable image-based interface elements. When a button with end caps is resized, the resizing occurs only in the middle of the button, in the region between the end caps. The end caps themselves keep their original size and appearance.

This property specifies the size of the top end cap. The middle (stretchable) portion is assumed to be 1 pixel wide. The bottom end cap is therefore computed by adding the size of the top end cap and the middle portion together and then subtracting that value from the height of the image:

```
bottomCapHeight = image.size.height - (image.topCapHeight + 1);
```

By default, this property is set to 0, which indicates that the image does not use end caps and the entire image is subject to stretching. To create a new image with a nonzero value for this property, use the stretchableImage(withLeftCapWidth:topCapHeight:) method.

## See Also

### Deprecated

func stretchableImage(withLeftCapWidth: Int, topCapHeight: Int) -> UIImage

Creates and returns a new image object with the specified cap values.

Deprecated

var leftCapWidth: Int

The horizontal end-cap size.

Deprecated

