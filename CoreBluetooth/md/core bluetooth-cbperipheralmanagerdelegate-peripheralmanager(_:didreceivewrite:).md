

- Core Bluetooth
- CBPeripheralManagerDelegate
-  peripheralManager(\_:didReceiveWrite:) 

Instance Method

# peripheralManager(\_:didReceiveWrite:)

Tells the delegate that a local peripheral device received an Attribute Protocol (ATT) write request for a characteristic with a dynamic value.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
optional func peripheralManager(
    _ peripheral: CBPeripheralManager,
    didReceiveWrite requests: [CBATTRequest]
)
```

## Parameters 

`peripheral`  

The peripheral manager that received the request.

`requests`  

A list of one or more CBATTRequest objects, each representing a request to write the value of a characteristic.

## Discussion

In the same way that you respond to a read request, each time you receive this callback, call the respond(to:withResult:) method of the CBPeripheralManager class exactly once. If the `requests` parameter contains multiple requests, treat them as you would a single request—if you can’t fulfill an individual request, you shouldn’t fulfill any of them. Instead, call the respond(to:withResult:) method immediately, and provide a result that indicates the cause of the failure.

When you respond to a write request, note that the first parameter of the respond(to:withResult:) method expects a single CBATTRequest object, even though you received an array of them from the peripheralManager(_:didReceiveWrite:) method. To respond properly, pass in the first request of the `requests` array.

## See Also

### Receiving Read and Write Requests

func peripheralManager(CBPeripheralManager, didReceiveRead: CBATTRequest)

Tells the delegate that a local peripheral received an Attribute Protocol (ATT) read request for a characteristic with a dynamic value.

