

- AVFoundation
- AVCapturePhoto
-  fileDataRepresentation(withReplacementMetadata:replacementEmbeddedThumbnailPhotoFormat:replacementEmbeddedThumbnailPixelBuffer:replacementDepthData:) Deprecated

Instance Method

# fileDataRepresentation(withReplacementMetadata:replacementEmbeddedThumbnailPhotoFormat:replacementEmbeddedThumbnailPixelBuffer:replacementDepthData:)

Generates and returns a flat data representation of the photo using the specified replacements for some or all of its attachments.

iOS 11.0–12.0DeprecatediPadOS 11.0–12.0DeprecatedMac Catalyst 13.1–13.1Deprecated

``` source
func fileDataRepresentation(
    withReplacementMetadata replacementMetadata: [String : Any]?,
    replacementEmbeddedThumbnailPhotoFormat: [String : Any]?,
    replacementEmbeddedThumbnailPixelBuffer: CVPixelBuffer?,
    replacementDepthData: AVDepthData?
) -> Data?
```

## Parameters 

`replacementMetadata`  

A dictionary (see `CGImageProperties` for possible keys and values) containing metadata to embed in the output file data.

To preserve existing metadata from the photo capture, pass this AVCapturePhoto object’s metadata dictionary. To discard metadata, pass `nil`.

`replacementEmbeddedThumbnailPhotoFormat`  

A dictionary (see Video Settings Dictionaries for possible keys and values) specifying the data format for a thumbnail preview image to embed in the output file data.

To preserve the existing thumbnail image from the photo capture, pass this AVCapturePhoto object’s embeddedThumbnailPhotoFormat dictionary. To discard the thumbnail, pass `nil`. (This parameter’s value must be consistent with that of the `replacementEmbeddedThumbnailPixelBuffer` parameter.)

`replacementEmbeddedThumbnailPixelBuffer`  

A pixel buffer containing a source image to be encoded to the file as the replacement thumbnail image.

To preserve the existing thumbnail image from the photo capture, pass `nil` for this parameter but pass this AVCapturePhoto object’s embeddedThumbnailPhotoFormat dictionary for the `replacementEmbeddedThumbnailPhotoFormat` parameter.

To discard the thumbnail, pass `nil` for both `replacementEmbeddedThumbnail` parameters.

`replacementDepthData`  

Replacement depth data to embed in the output file data.

To preserve the existing depth data from the photo capture (if any), pass this AVCapturePhoto object’s depthData object. To discard depth data, pass `nil`.

## Return Value

Data appropriate for writing to a file of the type specified when requesting photo capture, or `nil` if the photo and attachment data cannot be flattened.

## Discussion

When you request a photo capture with the AVCapturePhotoOutput capturePhoto(with:delegate:) method, the AVCapturePhotoSettings object you provide specifies image data formats (such as JPEG and HEVC) and container file formats (such as JFIF and HEIF) for the resulting image file. Calling this method formats and packages the image pixel buffer, along with metadata and other attachments created during capture (such as preview photos and depth maps), into data appropriate for writing to a file of that type.

This method is equivalent to the fileDataRepresentation() method, but allows you to replace attachments (metadata, preview thumbnail, or depth data) captured along with the photo with alternative data.

## See Also

### Packaging Data for File Output

func fileDataRepresentation(with: any AVCapturePhotoFileDataRepresentationCustomizer) -> Data?

Gets a customized representation of the photo data.

protocol AVCapturePhotoFileDataRepresentationCustomizer

A protocol that defines the methods to implement to customize the packaging of photo data.

func fileDataRepresentation() -> Data?

Generates and returns a flat data representation of the photo and its attachments.

func cgImageRepresentation() -> CGImage?

Extracts and returns the captured photo’s primary image as a Core Graphics image object.

func previewCGImageRepresentation() -> CGImage?

Extracts and returns the captured photo’s preview image as a Core Graphics image object.

