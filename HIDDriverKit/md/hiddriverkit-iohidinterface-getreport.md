

- HIDDriverKit
- IOHIDInterface
-  GetReport 

Instance Method

# GetReport

Retrieves a new input report from the HID device.

DriverKit 19.0+macOS

``` source
kern_return_t GetReport(IOMemoryDescriptor * report, IOHIDReportType reportType, uint32_t reportID, IOOptionBits options);
```

## Parameters 

`report`  

The memory descriptor in which to store the report data. On output, this descriptor contains the bytes of the report.

`reportType`  

The type of report you want.

`reportID`  

The unique identifier for the report.

`options`  

Options to specify when requesting the report.

## Return Value

kIOReturnSuccess on success, or another value if an error occurs. See Error Codes.

## Discussion

This method requests the report by calling the getReport method of its associated IOHIDDevice object. When getting the report from the device, this method combines the `reportID` and `options` together, with the `reportID` occupying the lower 8 bits of a 32-bit integer, and the `options` occupying the upper 24 bits.

## See Also

### Getting and Setting Input Reports

ReportAvailable

Notifies the interface that an updated report is available from the HID device.

AddReportToPool

Adds a memory descriptor to the report pool.

processReport

Parses the contents of the specified report and updates the interface’s elements.

SetReport

Sends a report to the HID device.

