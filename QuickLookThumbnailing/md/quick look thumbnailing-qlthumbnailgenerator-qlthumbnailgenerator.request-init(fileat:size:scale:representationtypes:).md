

- Quick Look Thumbnailing
- QLThumbnailGenerator
- QLThumbnailGenerator.Request
-  init(fileAt:size:scale:representationTypes:) 

Initializer

# init(fileAt:size:scale:representationTypes:)

Creates a new request for a thumbnail with the specified parameters for a file at a provided URL.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+visionOS 1.0+

``` source
init(
    fileAt url: URL,
    size: CGSize,
    scale: CGFloat,
    representationTypes: QLThumbnailGenerator.Request.RepresentationTypes
)
```

## Parameters 

`url`  

The URL of the file for which you want to create a thumbnail.

`size`  

The desired size of the thumbnails.

`scale`  

The scale of the thumbnails. This parameter usually represents the scale of the current screen. However, you can pass a screen scale to the initializer that isn’t the current device’s screen scale. For example, you can create thumbnails for different scales and upload them to a server in order to download them later on devices with a different screen scale.

`representationTypes`  

The different thumbnail types. For a list of all possible thumbnail representation types, see QLThumbnailGenerator.Request.RepresentationTypes.

## Return Value

An initialized request object to create a thumbnail for a file.

