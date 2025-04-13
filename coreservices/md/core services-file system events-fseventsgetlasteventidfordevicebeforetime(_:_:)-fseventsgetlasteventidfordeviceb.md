

- Core Services
- File System Events
-  FSEventsGetLastEventIdForDeviceBeforeTime(\_:\_:) 

Function

# FSEventsGetLastEventIdForDeviceBeforeTime(\_:\_:)

Mac Catalyst 13.1+macOS 10.5+

``` source
func FSEventsGetLastEventIdForDeviceBeforeTime(
    _ dev: dev_t,
    _ time: CFAbsoluteTime
) -> FSEventStreamEventId
```

## Parameters 

`dev`  

The dev_t of the device.

`time`  

The time as a CFAbsoluteTime whose value is the number of seconds since Jan 1, 1970 (i.e. a posix style time_t).

## Return Value

The last event ID for the given device that was returned before the given time.

## Discussion

Gets the last event ID for the given device that was returned before the given time. This is conservative in the sense that if you then use the returned event ID as the sinceWhen parameter of FSEventStreamCreateRelativeToDevice() that you will not miss any events that happened since that time. On the other hand, you might receive some (harmless) extra events.

Beware: there are things that can cause this to fail to be accurate. For example, someone might change the system's clock (either backwards or forwards). Or an external drive might be used on different systems without perfectly synchronized clocks.

