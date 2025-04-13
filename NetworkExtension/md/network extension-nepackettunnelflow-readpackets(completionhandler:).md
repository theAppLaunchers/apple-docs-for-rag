

- Network Extension
- NEPacketTunnelFlow
-  readPackets(completionHandler:) 

Instance Method

# readPackets(completionHandler:)

Reads IP packets from the TUN interface.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 17.0+visionOS 1.0+

``` source
func readPackets(completionHandler: @escaping ([Data], [NSNumber]) -> Void)
```

``` source
func readPackets() async -> ([Data], [NSNumber])
```

## Parameters 

`completionHandler`  

A Swift closure or an ObjectiveC block that runs when some packets are read from the TUN interface. The packets that were read are passed to this block in the `packets` array. The protocol numbers of the packets that were read are passed to this block in the `protocols` array. Each packet has a protocol number in the corresponding index in the `protocols` array. The protocol numbers are given in host byte order. Valid protocol numbers include `AF_INET` and `AF_INET6`. See `/usr/include/sys/socket.h`.

## Discussion

Each call to this method results in a single execution of the completion handler. The caller should call this method after each `completionHandler` execution in order to continue to receive packets from the TUN interface.

## See Also

### Handling IP packets

func readPacketObjects(completionHandler: ([NEPacket]) -> Void)

Read multiple IP packets from the TUN interface.

func writePacketObjects([NEPacket]) -> Bool

Write multiple IP packets to the TUN interface.

func writePackets([Data], withProtocols: [NSNumber]) -> Bool

Writes IP packets to the TUN interface.

