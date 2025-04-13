

- HIDDriverKit
- IOUserHIDEventService
-  dispatchDigitizerTouchEvent 

Instance Method

# dispatchDigitizerTouchEvent

Dispatches a digitizer touch event to the system.

DriverKit 19.0+macOS

``` source
kern_return_t dispatchDigitizerTouchEvent(uint64_t timeStamp, IOHIDDigitizerTouchData * touchData, uint32_t touchDataCount);
```

## Parameters 

`timeStamp`  

The timestamp of the event. Use the timestamp of the report element that is the source of the event.

`touchData`  

An array of structures containing the data for the individual touches. For more information, see IOHIDDigitizerTouchData.

`touchDataCount`  

The number of structures in the `touchData` parameter.

## Return Value

kIOReturnSuccess on success, or another value if an error occurs. See Error Codes.

## Discussion

Call this method from your event service to dispatch a touch event to the system. Typically, you call this method when handling a report from the device, after you determine that the event originated from a touchscreen or touch pad.

## See Also

### Dispatching Events to the System

dispatchDigitizerStylusEvent

Dispatches a digitizer stylus event to the system.

