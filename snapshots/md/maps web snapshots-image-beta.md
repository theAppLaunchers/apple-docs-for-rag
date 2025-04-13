

- Maps Web Snapshots
-  Image Beta

Object

# Image

A JSON object for a Snapshot URL that describes the characteristics of custom images to use for map annotations.

Maps Web Snapshots 1.0+Beta

## Properties

`url`

`string`

A required property that takes the full URL that specifies the location of the image. As an alternative, you may provide a data URL.

`height`

`integer`

The height of the image in scale-independent pixels. This property only required when referencing an annotation with `“markerStyle”: ”img”`.

`width`

`integer`

The width of the image in scale-independent pixels. This property only required when referencing an annotation with `“markerStyle”: ”img”`.

## Discussion

Maps Web Snapshots API supports JPEG, PNG, and GIF image formats for providing custom annotations. You may use up to 10 unique images in a snapshot request, and you may use an image for more than one annotation. It’s a good idea to use a URL shortener for image URLs so you don’t exceed the maximum character limit for a Snapshots URL.

If an image fails to load in a reasonable amount of time, the snapshot rendering uses the default “balloon” style marker.

Important

By providing an image URL, you’re responsible for ensuring the availability of the image at all times.

## See Also

### Essentials

Generating a URL and Signature to Create a Maps Web Snapshot

Create a Snapshot URL and generate a signature to validate the request.

object Annotation

An object for a Snapshot URL that describes annotation characteristics.

Beta

object Overlay

A JSON object for a Snapshot URL that describes overlay shape characteristics, including points for the overlay and styles such as width, color, and dash pattern.

Beta

object OverlayStyle

A JSON object that describes reusable styles for an overlay.

Beta

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

Learn more about using Apple's beta software 

