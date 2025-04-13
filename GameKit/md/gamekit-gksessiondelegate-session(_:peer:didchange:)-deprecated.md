

- GameKit
- GKSessionDelegate
-  session(\_:peer:didChange:) Deprecated

Instance Method

# session(\_:peer:didChange:)

Received by the delegate when a peer changes state.

macOS 10.8–10.10DeprecatedvisionOS 1.0–1.0DeprecatedwatchOS 2.0–2.0Deprecated

``` source
optional func session(
    _ session: GKSession,
    peer peerID: String,
    didChange state: GKPeerConnectionState
)
```

## Parameters 

`session`  

The session that received the update.

`peerID`  

A string that identifies the peer.

`state`  

The state the peer changed to.

## Discussion

A session calls this method whenever a visible peer changes it state relative to itself. The action your delegate should take depends on what state the peer moved to.

- When a peer first becomes visible to the session, it appears with a state of GKPeerStateAvailable. Your application should show this peer in its user interface. If the peer changes its state to GKPeerStateUnavailable, it no longer accepts connection requests and your application should remove it from the user interface.

- The delegate should ignore GKPeerStateConnecting changes and implement the session(_:didReceiveConnectionRequestFromPeer:) method instead.

- When a peer is connected (GKPeerStateConnected), your application may send data to the peer and receive data from the peer. If a connection to a peer is lost or if the peer deliberately disconnects (GKPeerStateDisconnected), your application should stop sending messages to this peer.

Important

If a GKPeerPickerController object is being used to configure the session, the controller handles updates for the GKPeerStateAvailable, GKPeerStateUnavailable, and GKPeerStateConnected states. Your delegate can ignore state changes if the peer picker dialog is in use.

