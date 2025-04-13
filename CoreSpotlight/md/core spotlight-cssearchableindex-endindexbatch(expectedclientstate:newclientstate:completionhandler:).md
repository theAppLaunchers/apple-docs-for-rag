

- Core Spotlight
- CSSearchableIndex
-  endIndexBatch(expectedClientState:newClientState:completionHandler:) 

Instance Method

# endIndexBatch(expectedClientState:newClientState:completionHandler:)

Ends a batch of index updates and stores the specified state information.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
func endIndexBatch(
    expectedClientState: Data?,
    newClientState: Data,
    completionHandler: (((any Error)?) -> Void)? = nil
)
```

``` source
func endIndexBatch(
    expectedClientState: Data?,
    newClientState: Data
) async throws
```

## Parameters 

`expectedClientState`  

The client state data from the previous batch.

`newClientState`  

Up to 250 bytes of app-specific data that can help you recover from a crash and resume indexing.

`completionHandler`  

The block to call with the results. The block receives the following parameter:

error  
If an error occurred, this parameter holds an error object that explains the error. Otherwise, the value of this parameter is `nil`.

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func endBatch(withClientState clientState: Data) async throws
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

## See Also

### Batching index updates

func beginBatch()

Begins a batch of updates to an index.

func endBatch(withClientState: Data, completionHandler: (((any Error)?) -> Void)?)

Ends a batch of index updates and stores the specified state information.

func fetchLastClientState(completionHandler: (Data?, (any Error)?) -> Void)

Fetches the app’s most recent client state information asynchronously.

