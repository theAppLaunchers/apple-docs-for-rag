

- ARKit
- ARWorldTrackingConfiguration
-  isCollaborationEnabled 

Instance Property

# isCollaborationEnabled

A flag that opts you in to a peer-to-peer multiuser AR experience.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+

``` source
var isCollaborationEnabled: Bool { get set }
```

## Discussion

The default value of this property is false. When you enable collaboration, ARKit invokes session(_:didOutputCollaborationData:) periodically, providing you with collaboration data to share with peers. Collaboration data contains information about the real-world surfaces ARKit detects, your position in relation to them, and any anchors you may have created.

Multiple users sharing collaboration data with each other results in an AR experience in which the users interact by sharing and manipulating anchors. By including information that describes a user’s unique view of the world, collaboration data enhances ARKit’s understanding of the layout of the physical environment much more quickly than is possible with only one user.

For more information, see Creating a collaborative session.

Important

Collaborative sessions work best with up to four participants.

### Sharing Collaboration Data Over the Network

You are responsible for sending collaboration data over the network, including choosing the network framework and implementing the code. See Creating a multiuser AR experience for an example app that shares a world map among users via Multipeer Connectivity. Although Creating a multiuser AR experience demonstrates sharing world data among peer users, it does so using a host-guest model. The primary advantage of collaboration data is that it enables you to share world data peer-to-peer.

The data you send is a serialized version of the ARSession.CollaborationData object provided by your session. You serialize it using NSKeyedArchiver.

```
func session(_ session: ARSession, didOutputCollaborationData data: ARSession.CollaborationData) {    
    if let collaborationDataEncoded = try? NSKeyedArchiver.archivedData(withRootObject: data, requiringSecureCoding: true) {
        multipeerSession.sendToAllPeers(collaborationDataEncoded)
    } else {
        fatalError("An error occurred while encoding collaboration data.")
    }
}
```

### Updating Your Session with Collaboration Data

When you receive collaboration data from other users, you instantiate an ARSession.CollaborationData object with it, and pass the object to your session via update(with:).

```
func receivedData(_ data: Data) {        
    if let collaborationData = try? NSKeyedUnarchiver.unarchivedObject(ofClass: ARSession.CollaborationData.self, from: data) {
        session.update(with: collaborationData)
    } else {
        fatalError("An error occurred while decoding collaboration data.")
    }
}

```

