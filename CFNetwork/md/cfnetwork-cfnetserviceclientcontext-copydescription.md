

- CFNetwork
- CFNetServiceClientContext
-  copyDescription 

Instance Property

# copyDescription

Callback used to create a descriptive string representation of the data pointed to by `info`. In implementing this function, return a reference to a CFString object that describes your allocator and some characteristics of your user-defined data, which is used by `CFCopyDescription()`. You can set this field to `NULL`, in which case Core Foundation will provide a rudimentary description.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.8+tvOS 9.0+visionOS 1.0+

``` source
var copyDescription: CFAllocatorCopyDescriptionCallBack?
```

## See Also

### Instance Properties

var info: UnsafeMutableRawPointer?

Arbitrary pointer to user-allocated memory containing user-defined data that is associated with the service, browser, or monitor and is passed to their respective callback functions. The data must be valid for as long as the CFNetService, CFNetServiceBrowser, or CFNetServiceMonitor is valid. Set this field to `NULL` if your callback function doesn’t want to receive user-defined data.

var release: CFAllocatorReleaseCallBack?

Callback that removes a retain previously added for the service or browser on the `info` pointer. This field can be `NULL`, but setting this field to `NULL` may result in memory leaks.

var retain: CFAllocatorRetainCallBack?

The callback used to add a retain for the service or browser using `info` for the life of the service or browser. This callback may be used for temporary references the service or browser needs to take. This callback returns the actual `info` pointer so it can be stored in the service or browser. This field can be `NULL`.

var version: CFIndex

Version number for this structure. Currently the only valid value is zero.

