

- RealityKit
- PhotogrammetrySession
- PhotogrammetrySession.Outputs
-  makeAsyncIterator() 

Instance Method

# makeAsyncIterator()

Creates an asynchronous iterator for the collection.

iOS 17.0+iPadOS 17.0+Mac Catalyst 15.0+macOS 12.0+

``` source
func makeAsyncIterator() -> PhotogrammetrySession.Outputs.Iterator
```

## Return Value

An asynchronous iterator.

## Discussion

This method creates an asynchronous iterator for the collection. Typically, you won’t call this method. Instead, use a `try`-`await`-`in` loop inside of an `async` task, which creates an iterator implicitly and waits for the session to publish new PhotogrammetrySession.Output objects, as the following example demonstrates.

```
let waiter = Task {
    do {
        for try await output in session.outputs {
            switch output {
                case .processingComplete:
                    // RealityKit has processed all requests.
                case .requestError(let request, let error):
                    // Request encountered an error.
                case .requestComplete(let request, let result):
                    // RealityKit has finished processing a request.
                case .requestProgress(let request, let fractionComplete):
                    // Periodic progress update. Update UI here.
                case requestProgressInfo(let request, let progressInfo):
                    // Periodic progress info update.
                case .inputComplete:
                    // Ingestion of images is complete and processing begins.
                case .invalidSample(let id, let reason):
                    // RealityKit deemed a sample invalid and didn't use it.
                case .skippedSample(let id):
                    // RealityKit was unable to use a provided sample.
                case .automaticDownsampling:
                    // RealityKit downsampled the input images because of
                    // resource constraints.
                case .processingCancelled
                    // Processing was canceled.
                @unknown default:
                    // Unrecognized output.
            }
        }
    } catch {
        print("Output: ERROR = \(String(describing: error))")
        // Handle error.
    }
}

```

## See Also

### Iterating the collection

typealias AsyncIterator

The type of asynchronous iterator that produces elements of this asynchronous sequence.

typealias Element

The type of element used for Photogrammetry Session updates.

struct Iterator

An object for iterating over published output objects.

