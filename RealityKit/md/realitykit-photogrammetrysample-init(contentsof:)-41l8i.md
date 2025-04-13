

- RealityKit
- PhotogrammetrySample
-  init(contentsOf:) 

Initializer

# init(contentsOf:)

Synchronously loads the image file located at URL into a `PhotogrammetrySample` with as many data fields populated as can be found in the target file. HEIC images captured with the `ObjectCaptureSession` will contain more advanced data fields beyond just the image. Which properties are populated depends on how the images were captured. The `id` of the sample will be automatically created to be unique to the current process. Throws: If `url` does not point to a file URL or there is a problem loading `url`.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+

``` source
init(contentsOf url: URL) throws
```

## Discussion

Note: this call will block the calling thread until it completes! It should not be called from the main thread or main actor, but can be useful if synchronous code is required. For use in an asynchronous context, please use the `init(contentsOf:) async throws` version.

This function is primarily used for creating a custom `Sequence` input for a `PhotogrammetrySession` which is synchronous but guaranteed by `PhotogrammetrySession` to be iterated off the main thread.

For example, we could compute and add an object mask to data captured with `ObjectCaptureSession` while preserving all other data. Here’s example code to make a lazy sequence using `init(contentsOf:)` to do this:

```
let inputSequence = myImageUrls.lazy.compactMap { file in
   do {
          var sample = try PhotogrammetrySample(contentsOf: file)
          sample.objectMask = myComputeObjectMask(image: sample.image)
          return sample
      } catch {
          print("Can't load sample: \(file)")
          return nil
      }
}
let session = PhotogrammetrySession(input: inputSequence)
 ...
```

