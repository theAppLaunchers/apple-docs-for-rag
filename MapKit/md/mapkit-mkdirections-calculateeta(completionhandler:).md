

- MapKit
- MKDirections
-  calculateETA(completionHandler:) 

Instance Method

# calculateETA(completionHandler:)

Begins calculating the requested travel-time information asynchronously.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.2+visionOS 1.0+

``` source
func calculateETA(completionHandler: @escaping MKDirections.ETAHandler)
```

``` source
func calculateETA() async throws -> MKDirections.ETAResponse
```

## Parameters 

`completionHandler`  

The block to execute when the travel-time estimate is ready or when an error occurs. This parameter can’t be `nil`.

## Discussion

Concurrency Note

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func calculateETA() async throws -> MKDirections.ETAResponse
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

This method initiates a request for a travel-time estimate and calls your completion handler block with the results. Travel-time estimates take much less time to generate than directions, so use this method in situations where you want a time estimate only. The method executes your completion handler on your app’s main thread. The implementation of your handler needs to check for errors and then incorporate the response data as appropriate.

If you call this method while a previous request is in process, this method calls your completion handler with an error. You can determine whether a request is in process by checking the value of the isCalculating property. You can also cancel a request as necessary.

## See Also

### Getting the ETA

typealias ETAHandler

The block to use for processing travel-time information.

class ETAResponse

The travel-time information that Apple servers return.

