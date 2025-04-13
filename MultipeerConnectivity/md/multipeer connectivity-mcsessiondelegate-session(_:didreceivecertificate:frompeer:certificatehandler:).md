

- Multipeer Connectivity
- MCSessionDelegate
-  session(\_:didReceiveCertificate:fromPeer:certificateHandler:) 

Instance Method

# session(\_:didReceiveCertificate:fromPeer:certificateHandler:)

Called to validate the client certificate provided by a peer when the connection is first established.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.10+tvOS 10.0+visionOS 1.0+

``` source
optional func session(
    _ session: MCSession,
    didReceiveCertificate certificate: [Any]?,
    fromPeer peerID: MCPeerID,
    certificateHandler: @escaping (Bool) -> Void
)
```

## Parameters 

`session`  

The session that the nearby peer wishes to join.

`certificate`  

A certificate chain, presented as an array of SecCertificateRef certificate objects. The first certificate in this chain is the peer’s certificate, which is derived from the identity that the peer provided when it called the init(peer:securityIdentity:encryptionPreference:) method. The other certificates are the (optional) additional chain certificates provided in that same array.

If the nearby peer did not provide a security identity, then this parameter’s value is `nil`.

`peerID`  

The peer ID of the sender.

`certificateHandler`  

Your app should call this handler with a value of true if the nearby peer should be allowed to join the session, or false otherwise.

## Discussion

Your app should inspect the nearby peer’s certificate, and then should decide whether to trust that certificate. Upon making that determination, your app should call the provided `certificateHandler` block, passing either true (to trust the nearby peer) or false (to reject it).

For information about validating certificates, read Cryptographic Services Guide.

Important

The multipeer connectivity framework makes no attempt to validate the peer-provided identity or certificates in any way. If your delegate does not implement this method, all certificates are accepted automatically.

## See Also

### MCSession Delegate Methods

func session(MCSession, didReceive: Data, fromPeer: MCPeerID)

Indicates that an `NSData` object has been received from a nearby peer.

**Required**

func session(MCSession, didStartReceivingResourceWithName: String, fromPeer: MCPeerID, with: Progress)

Indicates that the local peer began receiving a resource from a nearby peer.

**Required**

func session(MCSession, didFinishReceivingResourceWithName: String, fromPeer: MCPeerID, at: URL?, withError: (any Error)?)

Indicates that the local peer finished receiving a resource from a nearby peer.

**Required**

func session(MCSession, didReceive: InputStream, withName: String, fromPeer: MCPeerID)

Called when a nearby peer opens a byte stream connection to the local peer.

**Required**

func session(MCSession, peer: MCPeerID, didChange: MCSessionState)

Called when the state of a nearby peer changes.

**Required**

