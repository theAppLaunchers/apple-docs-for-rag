

- Network
- NWProtocolWebSocket
- NWProtocolWebSocket.Options
-  setSubprotocols(\_:) 

Instance Method

# setSubprotocols(\_:)

Adds to the list of supported application protocols that will be presented to a WebSocket server during connection establishment.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func setSubprotocols(_ subprotocols: [String])
```

## See Also

### Configuring Client Handshakes

func setAdditionalHeaders([(name: String, value: String)])

Sets additional HTTP header fields to be sent by the client during the WebSocket handshake.

var skipHandshake: Bool

A Boolean indicating whether the WebSocket protocol skips its handshake and begins framing data once the underlying connection is established.

