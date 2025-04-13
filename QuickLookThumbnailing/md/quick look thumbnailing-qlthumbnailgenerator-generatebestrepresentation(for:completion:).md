

- Quick Look Thumbnailing
- QLThumbnailGenerator
-  generateBestRepresentation(for:completion:) 

Instance Method

# generateBestRepresentation(for:completion:)

Generates the best possible thumbnail representation for a file and calls a handler upon completion.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+visionOS 1.0+

``` source
func generateBestRepresentation(
    for request: QLThumbnailGenerator.Request,
    completion completionHandler: @escaping (QLThumbnailRepresentation?, (any Error)?) -> Void
)
```

``` source
func generateBestRepresentation(for request: QLThumbnailGenerator.Request) async throws -> QLThumbnailRepresentation
```

## Parameters 

`request`  

The request that contains information about the thumbnail that you want to create.

`completionHandler`  

The completion handler to call when the thumbnail generation completes. It is always called when `QLThumbnailGenerator` finishes the generation of a requested thumbnail.

The completion handler takes the following parameters:

`thumbnail`  
The most representative version of the requested thumbnail or `nil` if `QLThumbnailGenerator` was unable to generate a thumbnail.

`error`  
An error object that indicates why the thumbnail generation failed, or `nil` if the thumbnail generation succeeded.

## Mentioned in 

Creating Quick Look Thumbnails to Preview Files in Your App

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func generateBestRepresentation(for request: QLThumbnailGenerator.Request) async throws -> QLThumbnailRepresentation
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

## See Also

### Generating a Thumbnail

func generateRepresentations(for: QLThumbnailGenerator.Request, update: ((QLThumbnailRepresentation?, QLThumbnailRepresentation.RepresentationType, (any Error)?) -> Void)?)

Generates various thumbnail representations for a file and calls the update handler for each thumbnail representation.

class Request

A request to generate a thumbnail for a file.

