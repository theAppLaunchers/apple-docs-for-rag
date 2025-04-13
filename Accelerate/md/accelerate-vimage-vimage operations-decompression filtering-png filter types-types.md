

- Accelerate
- vImage
- vImage Operations
- Decompression Filtering
-  PNG Filter Types 

API Collection

# PNG Filter Types

Filtering algorithms to apply to image data before compressing the data.

## Topics

### Constants

var kvImage_PNG_FILTER_VALUE_NONE: Int

No filtering.

var kvImage_PNG_FILTER_VALUE_SUB: Int

A filter that computes the difference between each byte of a pixel and the value of the corresponding byte of the pixel located to the left.

var kvImage_PNG_FILTER_VALUE_UP: Int

A filter that computes the difference between each byte of a pixel and the value of the corresponding byte of the pixel located above.

var kvImage_PNG_FILTER_VALUE_AVG: Int

A filter that predicts a pixel value from the average of the pixels to the left and above the predicted pixel location.

var kvImage_PNG_FILTER_VALUE_PAETH: Int

A filter that predicts a pixel value by applying a linear function to the pixels located to the left, above, and to the upper-left of the predicted pixel location.

