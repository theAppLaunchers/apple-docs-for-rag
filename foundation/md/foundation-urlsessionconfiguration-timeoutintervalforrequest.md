

- Foundation
- URLSessionConfiguration
-  timeoutIntervalForRequest 

Instance Property

# timeoutIntervalForRequest

The timeout interval to use when waiting for additional data.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var timeoutIntervalForRequest: TimeInterval { get set }
```

## Discussion

This property determines the request timeout interval for all tasks within sessions based on this configuration. The request timeout interval controls how long (in seconds) a task should wait for additional data to arrive before giving up. The timer associated with this value is reset whenever new data arrives. When the request timer reaches the specified interval without receiving any new data, it triggers a timeout.

The default value is `60`.

Important

Any upload or download tasks created by a background session are automatically retried if the original request fails due to a timeout. To configure how long an upload or download task should be allowed to be retried or transferred, use the timeoutIntervalForResource property.

## See Also

### Setting general properties

var identifier: String?

The background session identifier of the configuration object.

var httpAdditionalHeaders: [AnyHashable : Any]?

A dictionary of additional headers to send with requests.

var networkServiceType: NSURLRequest.NetworkServiceType

The type of network service for all tasks within network sessions to enable Cellular Network Slicing.

var allowsCellularAccess: Bool

A Boolean value that determines whether connections should be made over a cellular network.

var timeoutIntervalForResource: TimeInterval

The maximum amount of time that a resource request should be allowed to take.

var sharedContainerIdentifier: String?

The identifier for the shared container into which files in background URL sessions should be downloaded.

var waitsForConnectivity: Bool

A Boolean value that indicates whether the session should wait for connectivity to become available, or fail immediately.

var usesClassicLoadingMode: Bool

