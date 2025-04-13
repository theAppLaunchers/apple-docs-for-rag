

- CarKey
- CarKeyRemoteControlSession
-  perform(\_:) 

Instance Method

# perform(\_:)

Sends a request to the vehicle to perform a one-time action.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.3+watchOS 9.0+

``` source
func perform(_ action: RemoteKeylessEntryAction) throws -> RemoteKeylessEntryAction.ExecutionRequest
```

## Parameters 

`action`  

The one-time action to perform. Use this object to specify the action you want to perform and the vehicle on which to perform it.

## Return Value

An object you use to get the results of the request.

## Discussion

Call this method when the vehicle feature involves a one-time action. For example, use it to lock the doors of the vehicle. This method sends the request to the vehicle asynchronously.

Use the returned object to get the execution status of the specified request. The execution status indicates whether the vehicle completed the action successfully or an error occurred.

## See Also

### Performing Vehicle-Related Actions

func perform(RemoteKeylessEntryEnduringAction) throws -> RemoteKeylessEntryEnduringAction.EnduringExecutionRequest

Sends a request to the vehicle to start an action that has a separate stopping point.

Deprecated

