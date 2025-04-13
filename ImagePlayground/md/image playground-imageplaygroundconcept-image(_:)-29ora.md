

- Image Playground
- ImagePlaygroundConcept
-  image(\_:) 

Type Method

# image(\_:)

Creates a concept structure from the specified image object.

iOS 18.1+iPadOS 18.1+Mac Catalyst 18.1+macOS 15.1+visionOS 2.4+

``` source
static func image(_ image: CGImage) -> ImagePlaygroundConcept
```

## Parameters 

`image`  

The image you want to pass to the diffusion model.

## Discussion

Call this method when you want to use an image as the basis for generating a new image. Typically, you include other text-based concept structures in addition to this one. Include at most one image among the collection of concepts. Including more than one image yields unpredictable image results.

## See Also

### Describing the image

static func text(String) -> ImagePlaygroundConcept

Creates a concept structure that includes a short text description.

static func extracted(from: String, title: String?) -> ImagePlaygroundConcept

Creates a concept structure from a long-form string and a title that guides the extraction of concepts from that string.

static func drawing(PKDrawing) -> ImagePlaygroundConcept

Creates a concept structure from a PencilKit drawing.

static func image(URL) -> ImagePlaygroundConcept?

Creates a concept structure from the image at the specified URL.

