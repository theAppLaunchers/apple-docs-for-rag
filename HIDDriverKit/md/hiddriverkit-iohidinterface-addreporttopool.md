

- HIDDriverKit
- IOHIDInterface
-  AddReportToPool 

Instance Method

# AddReportToPool

Adds a memory descriptor to the report pool.

DriverKit 19.0+macOS

``` source
kern_return_t AddReportToPool(IOBufferMemoryDescriptor * report);
```

## Parameters 

`report`  

A memory descriptor large enough to hold input reports from the device. The interface writes zeros to the descriptor’s bytes before using it to store a new input report.

## Return Value

kIOReturnSuccess on success, or another value if an error occurs. See Error Codes.

## Discussion

When implementing a custom driver or event service, call this method to add one or more memory descriptors to a shared resource pool. When an input report arrives from the device, the interface removes a memory descriptor from the pool, fills it with the report data, and calls the ReportAvailable method of the session’s action object.

You are responsible for ensuring the pool has enough memory descriptors to store incoming reports. One way to maintain a sufficient supply of memory descriptors is to recycle them. In your action object’s `ReportAvailable` method, process the report and add the provided memory descriptor back to the pool when you are done.

## See Also

### Getting and Setting Input Reports

ReportAvailable

Notifies the interface that an updated report is available from the HID device.

processReport

Parses the contents of the specified report and updates the interface’s elements.

GetReport

Retrieves a new input report from the HID device.

SetReport

Sends a report to the HID device.

