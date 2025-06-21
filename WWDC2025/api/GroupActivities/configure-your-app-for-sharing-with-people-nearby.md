*   [Group Activities](/documentation/groupactivities)
*   Configure your visionOS app for sharing with people nearby

Article

# Configure your visionOS app for sharing with people nearby

Create shared experiences for people wearing Vision Pro in the same room and those on FaceTime.

## [Overview](/documentation/GroupActivities/configure-your-app-for-sharing-with-people-nearby#Overview)

SharePlay in visionOS helps people share activities together — for example, viewing a movie, listening to music, playing a game, or sketching ideas on a whiteboard. Starting in visionOS 26, SharePlay supports inviting nearby people who are wearing Apple Vision Pro to join a group activity. The system presents participants differently based on how they join the activity:

*   Nearby participants appear naturally via passthrough.
    
*   FaceTime participants who are wearing Apple Vision Pro appear as spatial Personas.
    
*   Participants on other devices appear in a standard FaceTime window.
    

Both nearby participants and spatial Personas can move spatially, make eye contact, and reference virtual content during an activity, enhancing the feeling of being together in the same room. Get your visionOS app ready for sharing with people nearby by reviewing the APIs below that help you create seamless connections among people — whether they’re in the same room or on FaceTime.

Note

If you’re new to SharePlay in visionOS, see [Building a guessing game for visionOS](/documentation/groupactivities/building-a-guessing-game-for-visionos) for a complete guide to building a visionOS SharePlay app.

### [Verify your app’s nearby-sharing behavior](/documentation/GroupActivities/configure-your-app-for-sharing-with-people-nearby#Verify-your-apps-nearby-sharing-behavior)

SharePlay doesn’t require apps to distinguish between nearby and FaceTime participants. The `GroupActivities` APIs you use to manage group sessions, exchange messages, and position content treat all participants the same. Your app doesn’t need separate code to support nearby participants, so it typically already works when sharing with people nearby, but confirm the following during testing:

Spatial assumptions

Confirm that your app doesn’t rely on the system to position nearby participants in specific locations. SharePlay can dynamically reposition spatial Personas (FaceTime participants), but not physical people (nearby participants). If your app requires participants to be in specific locations, guide nearby participants to move to those locations using visual cues, like position markers.

Share Window menu

Confirm that your activity is listed in the new Share Window menu located next to the window bar. This is critical for the discovery of your app’s SharePlay activity. The easiest way to add your activity to the Share Window menu is to include a hidden [`ShareLink`](/documentation/SwiftUI/ShareLink) in your app.

```

```
ShareLink(item: BoardGameActivity(), preview: SharePreview("Play Together"))
    .hidden()
```

```

For more information, see [Presenting SharePlay activities from your app’s UI](/documentation/groupactivities/promoting-shareplay-activities-from-your-apps-ui).

Activity activation

If your app implements a custom SharePlay button, confirm that your app supports initiating an activity when there isn’t an active FaceTime call. For visionOS, update the button’s action handler to always call [`activate()`](/documentation/groupactivities/groupactivity/activate\(\)), which now presents the new Share Window menu, and remove any checks for [`isEligibleForGroupSession`](/documentation/groupactivities/groupstateobserver/iseligibleforgroupsession) that guard activating the activity.

Important

To start your activity from the system’s Share Window menu, you need to donate it. If you don’t donate your activity, the system defaults to window mirroring instead of SharePlay.

### [Distinguish between nearby and FaceTime participants](/documentation/GroupActivities/configure-your-app-for-sharing-with-people-nearby#Distinguish-between-nearby-and-FaceTime-participants)

To observe when participants join and leave an activity use [`activeParticipants`](/documentation/groupactivities/groupsession/activeparticipants). To determine if a [`Participant`](/documentation/groupactivities/participant) is nearby, use [`isNearbyWithLocalParticipant`](/documentation/groupactivities/participant/isnearbywithlocalparticipant):

```swift
```swift
```swift
```swift
```swift
```swift
func observeParticipants(session: GroupSession<BoardGameActivity>) async {
```
```
    for await activeParticipants in session.$activeParticipants.values {
        // The set of nearby participants, excluding the local participant.
        let nearbyParticipants = activeParticipants.filter {
            $0.isNearbyWithLocalParticipant && $0.id != session.localParticipant.id
        }
    }
}
```
```
```
```

### [Position content relative to participants](/documentation/GroupActivities/configure-your-app-for-sharing-with-people-nearby#Position-content-relative-to-participants)

Because nearby participants can join a group activity, you can no longer assume a spatial participant’s pose (position and orientation) matches their seat’s pose. When SharePlay applies a [`SpatialTemplate`](/documentation/groupactivities/spatialtemplate), it moves FaceTime participants using their spatial Persona to their assigned seats so their pose matches their seat’s pose. SharePlay can’t move a nearby participant, so the participant’s pose can be different from their seat’s pose.

*   To observe the state of remote FaceTime and nearby participants use [`remoteParticipantStates`](/documentation/groupactivities/systemcoordinator/remoteparticipantstates).
    
*   To observe the state of the local participant, who is wearing Vision Pro, use [`localParticipantStates`](/documentation/groupactivities/systemcoordinator/localparticipantstates).
    
*   To position content relative to a participant, position the content relative to [`ParticipantState.pose`](/documentation/groupactivities/systemcoordinator/participantstate/pose).
    
*   To position content relative to a participant’s seat, position the content relative to [`ParticipantState.seat.pose`](/documentation/groupactivities/systemcoordinator/participantstate/seat-swift.struct/pose).
    

Note

A participant’s pose and seat pose are snapshots, not continuous tracking data. They are updated by the system at various points throughout a session, for example, when a new [`SpatialTemplate`](/documentation/groupactivities/spatialtemplate) is applied by the system or when a participant recenters.

### [Synchronize entity transforms across devices](/documentation/GroupActivities/configure-your-app-for-sharing-with-people-nearby#Synchronize-entity-transforms-across-devices)

To achieve consistent positioning of RealityKit entities across multiple devices in an immersive space during a SharePlay session, enable support for a group immersive space using [`SystemCoordinator.Configuration.supportsGroupImmersiveSpace`](/documentation/groupactivities/systemcoordinator/configuration-swift.struct/supportsgroupimmersivespace). When enabled, visionOS automatically ensures entities with identical transforms appear in the same relative location for all participants, including both nearby and remote participants.

Group immersive spaces handle this spatial consistency for entities with identical transforms, but keep in mind that SharePlay doesn’t automatically synchronize changes to your app’s state. Your app needs to maintain visual consistency across participants’ devices and you have full control over what actions are synchronized. For example, if your app displays a cube with a position of `[0, 1, 0]` at launch, the shared coordinate system causes everyone to see that cube at the same position. However, if a participant creates a new cube, your app needs to use the [`GroupSessionMessenger`](/documentation/groupactivities/groupsessionmessenger) to notify the other participants to reflect this change.

### [Incorporate the real world in your app’s shared context](/documentation/GroupActivities/configure-your-app-for-sharing-with-people-nearby#Incorporate-the-real-world-in-your-apps-shared-context)

When you’re sharing with people who are nearby, you may want to anchor shared virtual content to objects in the real world. Unlike remote SharePlay with spatial Personas, when you’re sharing with someone nearby, the real world is part of your shared context. To enable this, ARKit has support for sharing world anchors that appear in the exact same place for all nearby participants.

To make a [`WorldAnchor`](/documentation/ARKit/WorldAnchor) shareable with nearby participants, initialize the anchor with the `isSharedWithNearbyParticipants` property set to `true` with the [`init(originFromAnchorTransform:sharedWithNearbyParticipants:)`](/documentation/ARKit/WorldAnchor/init\(originFromAnchorTransform:sharedWithNearbyParticipants:\)) initializer. ARKit then shares that anchor with all nearby SharePlay participants via the [`anchorUpdates`](/documentation/ARKit/WorldTrackingProvider/anchorUpdates) async sequence.

Your app can then attach an entity to that anchor to place it in the exact same world location for all nearby participants.

```swift

```swift
// Create a shared world anchor with ARKit.
```swift
```swift
func setUp(session: ARKitSession, provider: WorldTrackingProvider) async throws {
```
```
    try await session.run([provider])
}
```swift
```swift
func createAnchor(
```
```
    at transform: simd_float4x4, 
    provider: WorldTrackingProvider
) async throws {
    // Create a world anchor with `sharedWithNearbyParticipants` set to `true`.
    let anchor = WorldAnchor(
        originFromAnchorTransform: transform,
        sharedWithNearbyParticipants: true
    )
    try await provider.addAnchor(anchor)
}
```swift
```swift
func observeWorldTracking(provider: WorldTrackingProvider) async {
```
```
    for await update in provider.anchorUpdates {
        switch update.event {
            case .added, .updated, .removed:
            // Updates with shared anchors from others.
            let anchorIdentifier = update.anchor.id
        }
    }
}
```

```

Important

ARKit does not share world anchors with remote participants. Apps still need to use [`GroupSessionMessenger`](/documentation/groupactivities/groupsessionmessenger) to fully synchronize the position of these entities with all spatial participants.

## [See Also](/documentation/GroupActivities/configure-your-app-for-sharing-with-people-nearby#see-also)

### [Spatial activities](/documentation/GroupActivities/configure-your-app-for-sharing-with-people-nearby#Spatial-activities)

[

Adding spatial Persona support to an activity](/documentation/groupactivities/adding-spatial-persona-support-to-an-activity)

Update your SharePlay activities to support spatial Personas and the shared context when running in visionOS.

```swift
```swift
```swift
class SystemCoordinator
```
```

A type you use to coordinate your interface’s behavior when an active SharePlay session supports spatial placement of content.
```
```swift
```swift
```swift
struct ParticipantState
```
```

A structure that tells you whether a participant supports a shared simulation space for the current activity.
```

[`nonisolated func groupActivityAssociation(_ kind: GroupActivityAssociationKind?) -> some View`](/documentation/SwiftUI/View/groupActivityAssociation\(_:\)) 

Specifies how a view should be associated with the current SharePlay group activity.

Beta

```swift
```swift
```swift
class GroupActivityAssociationInteraction
```
```

An interaction configures a view’s association with the current SharePlay group activity.

Beta
```
```swift
```swift
```swift
struct GroupActivityAssociationKind
```
```

An association a user-interface element can have with a SharePlay group activity.

Beta
```