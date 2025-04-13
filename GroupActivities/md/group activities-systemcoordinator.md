

- Group Activities
-  SystemCoordinator 

Class

# SystemCoordinator

A type you use to coordinate your interface’s behavior when an active SharePlay session supports spatial placement of content.

visionOS 1.0+

``` source
final class SystemCoordinator
```

## Mentioned in 

Adding spatial Persona support to an activity

## Overview

A SystemCoordinator object helps you coordinate the presentation of your app’s content when spatial placement is active. In visionOS, the system can present a SharePlay activity as if the participants were together in the same room with the content. Each participant views the content from a particular vantage point, and sees the changes that others make. The system handles the placement of each participant’s spatial Persona relative to the content, but you handle any changes to the content itself with the help of the SystemCoordinator object.

You don’t create a SystemCoordinator object directly. After you receive a GroupSession object for an activity, retrieve the system coordinator from the session’s systemCoordinator property. When you first retrieve the object, update its configuration property to tell the system how you want to arrange participants in the scene. After that, use the information in the system coordinator’s properties to keep your app’s interface up to date. When participants support spatial placement, send additional data to synchronize your content for those participants. For example, when one person scrolls the contents of a window, update the scroll position in the window of other spatially aware participants to preserve the shared context for everyone.

You choose what information to share among participants, and you choose how to manage the corresponding updates. A system coordinator object only helps you know when to make those changes. Observe the object’s published properties to receive automatic updates when the values change.

## Topics

### Configuring the system coordinator

var configuration: SystemCoordinator.Configuration

The current configuration of the system coordinator.

struct Configuration

A structure that specifies your app’s support for activities that take place in a shared simulation space.

### Getting the participant state

var localParticipantState: SystemCoordinator.ParticipantState

The current participant’s level of support for an activity that takes place in a shared simulation space.

var localParticipantStates: SystemCoordinator.ParticipantStates

An asynchronous sequence that reports changes to the local participant’s state.

struct ParticipantStates

An asynchronous sequence that reports the current person’s ability to participate in a shared context.

### Getting the current immersion level

var groupImmersionStyle: SystemCoordinator.GroupImmersionStyles

The presentation style to apply to an immersive space for the current activity.

struct GroupImmersionStyles

An asynchronous sequence that contains one or more incoming immersion styles for you to process.

### Assigning the local participant role

func assignRole(some SpatialTemplateRole)

Assigns the given spatial template role to the local participant.

func resignRole()

Resigns the local participant from their current spatial template role.

### Structures

struct ParticipantState

A structure that tells you whether a participant supports a shared simulation space for the current activity.

## Relationships

### Conforms To

- Sendable

## See Also

### Spatial activities

Adding spatial Persona support to an activity

Update your SharePlay activities to support spatial Personas and the shared context when running in visionOS.

struct ParticipantState

A structure that tells you whether a participant supports a shared simulation space for the current activity.

