

- Paravirtualized Graphics
-  PGAddTraceRange 

Type Alias

# PGAddTraceRange

The block signature for a routine that adds a trace range.

Mac Catalyst 14.0+macOS 11.0+

``` source
typealias PGAddTraceRange = (UnsafeMutablePointer, @escaping PGTraceRangeHandler) -> OpaquePointer?
```

## Parameters 

`range`  

The range of guest physical memory to monitor.

`handler`  

The block for the app to call when it detects any writes to the memory range.

## Return Value

A PGTraceRange_t pointer, or `NULL` if an error occurred.

## Discussion

The framework uses traces to provide a low-overhead framebuffer implementation that the virtual graphics device uses before the guest OS loads the driver.

The block also records any data it needs to keep track of this trace and returns a pointer to that data. The framework doesn’t read from this pointer.

Until the framework destroys the trace, the app must detect whenever the guest alters the contents of memory within the trace range. When the app detects memory changes, call the handler to notify the framework. Where possible, coalesce the handling of these notifications over a period of several milliseconds to reduce the number of calls to the handler.

## See Also

### Specifying Trace Behavior

var addTraceRange: PGAddTraceRange?

A handler that the framework calls to add a trace range.

var removeTraceRange: PGRemoveTraceRange?

A handler that the framework calls to remove a trace range.

typealias PGRemoveTraceRange

The block signature for a routine that removes a trace range.

typealias PGTraceRangeHandler

The block signature for a routine that handles trace requests.

