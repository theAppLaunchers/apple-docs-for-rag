

- Matter
- MTRDeviceControllerServerProtocol
-  invokeCommand(withController:nodeId:endpointId:clusterId:commandId:fields:timedInvokeTimeout:completion:) 

Instance Method

# invokeCommand(withController:nodeId:endpointId:clusterId:commandId:fields:timedInvokeTimeout:completion:)

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.1+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
func invokeCommand(
    withController controller: Any?,
    nodeId: UInt64,
    endpointId: NSNumber,
    clusterId: NSNumber,
    commandId: NSNumber,
    fields: Any,
    timedInvokeTimeout timeoutMs: NSNumber?,
    completion: @escaping MTRValuesHandler
)
```

``` source
func invokeCommand(
    withController controller: Any?,
    nodeId: UInt64,
    endpointId: NSNumber,
    clusterId: NSNumber,
    commandId: NSNumber,
    fields: Any,
    timedInvokeTimeout timeoutMs: NSNumber?
) async throws -> Any
```

**Required**

## Discussion

Concurrency Note

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func invokeCommand(withController controller: Any?, nodeId: UInt64, endpointId: NSNumber, clusterId: NSNumber, commandId: NSNumber, fields: Any, timedInvokeTimeout timeoutMs: NSNumber?) async throws -> Any
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

