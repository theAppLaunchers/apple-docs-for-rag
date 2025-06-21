Framework

# Group Activities

Create app-specific activities your users can share and experience together.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

## [Overview](/documentation/groupactivities#Overview)

With the Group Activities framework, you can provide your app’s content in SharePlay experiences, which create a sense of connection and immediacy for your users. For example, a video-streaming app might offer the ability to attend movie-watching parties in which participants watch simultaneously from their personal devices. The app handles the playback on each device, but the Group Activities framework synchronizes that playback and facilitates communication between the devices.

This framework leverages the FaceTime infrastructure to synchronize your app’s activities and to invite other participants to join those activities. When your app’s UI contains shareable activities, adopt the [`GroupActivity`](/documentation/groupactivities/groupactivity) protocol in the objects you use to represent those activities. When a group activity begins, use the [`GroupSession`](/documentation/groupactivities/groupsession) object to synchronize your app’s behavior with other participating devices.

Note

The Group Activities framework uses end-to-end encryption on all session data that the [`GroupSession`](/documentation/groupactivities/groupsession) object synchronizes between devices. Apple doesn’t have the keys to decrypt this data. Your use of the Group Activities framework doesn’t provide Apple with visibility into the content your app shares, or information related to playback of media content in your app, such as where in the content a user starts, pauses, or skips a session. Apple servers facilitating Group Activities sessions don’t know the identity of your app. Occasionally, Apple may ask a small number of users to help troubleshoot issues, such as by [capturing a sysdiagnose or installing a debugging profile](https://developer.apple.com/bug-reporting/profiles-and-logs/), which may incidentally result in Apple collecting some information related to content shared in your app.

## [Topics](/documentation/groupactivities#topics)

### [Essentials](/documentation/groupactivities#Essentials)

[`com.apple.developer.group-session`](/documentation/BundleResources/Entitlements/com.apple.developer.group-session)

A Boolean value that indicates whether the app may implement shared group experiences.

### [Activity definition](/documentation/groupactivities#Activity-definition)

[

Defining your app’s SharePlay activities](/documentation/groupactivities/defining-your-apps-shareplay-activities)

Configure your app’s SharePlay support and define the activities that people can perform from your app.

[

Supporting Coordinated Media Playback](/documentation/AVFoundation/supporting-coordinated-media-playback)

Create synchronized media experiences that enable users to watch and listen across devices.

```swift
```swift
```swift
protocol GroupActivity
```
```

A type that can advertise your app’s activities to other participants.
```
```swift
```swift
```swift
struct GroupActivityMetadata
```
```

Text and image content that describes an activity to potential participants.
```
```swift
```swift
```swift
enum GroupActivityActivationResult
```
```

The result of preparing to start a custom activity.
```
```swift
```swift
```swift
struct GroupActivityTransferRepresentation
```
```

A type that lets you start a group activity from a known context.
```

### [Interface presentation](/documentation/groupactivities#Interface-presentation)

[

Presenting SharePlay activities from your app’s UI](/documentation/groupactivities/promoting-shareplay-activities-from-your-apps-ui)

Make it easy for people to start activities from your app’s UI, from the system share sheet, or using AirPlay over AirDrop.

```swift
```swift
```swift
class GroupActivitySharingController
```
```

A macOS view controller that displays the system interface for starting an activity, and optionally starts a FaceTime call for that activity.
```
```swift
```swift
```swift
class GroupActivitySharingController
```
```

An iOS view controller that displays the system interface for starting an activity, and optionally starts a FaceTime call for that activity.
```

### [Session management](/documentation/groupactivities#Session-management)

[

Joining and managing a shared activity](/documentation/groupactivities/joining-and-managing-a-shared-activity)

Configure the session when a SharePlay activity starts, and handle events that occur during the lifetime of the activity.

[

Drawing content in a group session](/documentation/groupactivities/drawing_content_in_a_group_session)

Invite your friends to draw on a shared canvas while on a FaceTime call.

```swift
```swift
```swift
class GroupSession
```
```

A session for an in-progress activity that synchronizes content among participant devices.
```
```swift
```swift
```swift
protocol CustomMessageIdentifiable
```
```

A type that assigns a custom ID string to messages you send to other devices.
```
```swift
```swift
```swift
struct Participant
```
```

An active participant in a group session.
```

### [Spatial activities](/documentation/groupactivities#Spatial-activities)

[

Configure your visionOS app for sharing with people nearby](/documentation/groupactivities/configure-your-app-for-sharing-with-people-nearby)

Create shared experiences for people wearing Vision Pro in the same room and those on FaceTime.

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

### [Custom spatial templates](/documentation/groupactivities#Custom-spatial-templates)

[

Building a guessing game for visionOS](/documentation/groupactivities/building-a-guessing-game-for-visionos)

Create a team-based guessing game for visionOS using Group Activities.

```swift
```swift
```swift
protocol SpatialTemplate
```
```

An interface you use to create custom arrangements of spatial Personas in a scene.
```
```swift
```swift
```swift
struct SpatialTemplatePreference
```
```

A structure that specifies the preferred arrangement of participant spatial Personas in a shared simulation space.
```
```swift
```swift
```swift
struct SpatialTemplateSeatElement
```
```

A spatial template element that represents a seat for a participant in the activity.
```
```swift
```swift
```swift
protocol SpatialTemplateElement
```
```

An interface that defines an element in your spatial template.
```
```swift
```swift
```swift
struct SpatialTemplateElementPosition
```
```

A type that defines the position of an element in a spatial template.
```
```swift
```swift
```swift
struct SpatialTemplateElementDirection
```
```

The initial direction a participant faces when an activity starts.
```
```swift
```swift
```swift
protocol SpatialTemplateRole
```
```

An interface for defining roles that you assign to the participants of a group activity.
```

### [File and data transfer](/documentation/groupactivities#File-and-data-transfer)

[

Synchronizing data during a SharePlay activity](/documentation/groupactivities/synchronizing-data-during-a-shareplay-activity)

Send custom messages and data between devices to synchronize content for your activity, and incorporate messages your app receives from other participants.

```swift
```swift
```swift
class GroupSessionMessenger
```
```

An object that transfers app-specific data between the devices joined in a group session.
```
```swift
```swift
```swift
class GroupSessionJournal
```
```

An object that manages file and data transfers between participants joined in a group session.
```

### [System status](/documentation/groupactivities#System-status)

```swift
```swift
```swift
```swift
class GroupStateObserver
```
```

An object that contains information about the system’s ability to start SharePlay experiences.
```
```