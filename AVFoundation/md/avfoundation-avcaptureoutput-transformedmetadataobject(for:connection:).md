

- AVFoundation
- AVCaptureOutput
-  transformedMetadataObject(for:connection:) 

Instance Method

# transformedMetadataObject(for:connection:)

Converts a metadata object’s visual properties to layer coordinates.

iOS 6.0+iPadOS 6.0+Mac Catalyst 14.0+macOS 10.15+tvOS 17.0+

``` source
func transformedMetadataObject(
    for metadataObject: AVMetadataObject,
    connection: AVCaptureConnection
) -> AVMetadataObject?
```

## Parameters 

`metadataObject`  

A metadata object that originates from the same capture input as the preview layer.

`connection`  

The output’s connection whose input matches that of the metadata object to convert.

## Return Value

A metadata object whose properties are in output coordinates, or `nil` if the object originates from an input source other than the preview layer.

## Discussion

A metadata object has a rectangular bounds where `0,0` is the top-left of the picture area, and `1,1` represents the bottom-right on an unrotated picture. Face metadata objects likewise express yaw and roll angles with respect to an unrotated picture.

This method converts the visual properties in the coordinate space of the supplied metadata object to the coordinate space of the output. The conversion takes orientation, mirroring, layer bounds and video gravity into consideration. If the provided metadata object originates from an input source other than the preview layer’s, the method returns `nil`.

## See Also

### Converting Between Coordinate Systems

func metadataOutputRectConverted(fromOutputRect: CGRect) -> CGRect

Converts a rectangle in the capture output object’s coordinate system to one in the coordinate system used for metadata outputs.

func outputRectConverted(fromMetadataOutputRect: CGRect) -> CGRect

Converts a rectangle in the coordinate system used for metadata outputs to one in the capture output object’s coordinate system.

