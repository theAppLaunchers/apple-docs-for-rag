

- AVFoundation
- AVPlayerItemAccessLogEvent
-  transferDuration 

Instance Property

# transferDuration

The accumulated duration, in seconds, of active network transfer of bytes.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 1.0+

``` source
var transferDuration: TimeInterval { get }
```

## Discussion

The value of the property is negative if unknown.

Corresponds to “c-transfer-duration”.

This property is not compatible with key-value observing.

## See Also

### Getting Server-Related Log Events

var uri: String?

The URI of the playback item.

var serverAddress: String?

The IP address of the server that was the source of the last delivered media segment.

var numberOfServerAddressChanges: Int

A count of changes to the server address over the last uninterrupted period of playback.

var mediaRequestsWWAN: Int

The number of network read requests over a WWAN.

var numberOfBytesTransferred: Int64

The accumulated number of bytes transferred by the item.

var numberOfMediaRequests: Int

The number of media read requests from the server to this client.

