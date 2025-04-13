

- Group Activities
- SystemCoordinator
-  SystemCoordinator.ParticipantState 

Structure

# SystemCoordinator.ParticipantState

A structure that tells you whether a participant supports a shared simulation space for the current activity.

visionOS 1.0+

``` source
struct ParticipantState
```

## Mentioned in 

Adding spatial Persona support to an activity

## Overview

A SystemCoordinator.ParticipantState structure reports the current person’s ability to display a spatial Persona when joined to a group activity. A person can display a spatial Persona only if the device supports it, and only if they configured that spatial Persona in advance.

When someone’s spatial Persona is active, SharePlay positions the person in the scene relative to the shared content. When that happens, share any extra activity-related details that preserve the shared context of the scene. For example, when one person scrolls the content in a shared window, communicate the new scroll position as an activity update. When your app receives those extra updates, apply them only if the current spatial Persona is also active.

Observe the participant’s spatial state from the localParticipantState property of your session’s SystemCoordinator object. Spatial state information can change, so update your app’s presentation to reflect the person’s current support for the activity.

## Topics

### Getting the participant details

let isSpatial: Bool

A Boolean value that indicates whether the person supports being in a shared simulation space for an activity.

### Structures

struct Seat

A seat assigned to a single participant in a spatial template.

### Operators

static func == (SystemCoordinator.ParticipantState, SystemCoordinator.ParticipantState) -> Bool

Returns a Boolean value indicating whether two values are equal.

### Instance Properties

let role: (any SpatialTemplateRole)?

The role assigned to this participant, if any.

let seat: SystemCoordinator.ParticipantState.Seat?

The seat assigned to this participant.

### Default Implementations

Equatable Implementations

## Relationships

### Conforms To

- Equatable
- Sendable

## See Also

### Spatial activities

Adding spatial Persona support to an activity

Update your SharePlay activities to support spatial Personas and the shared context when running in visionOS.

class SystemCoordinator

A type you use to coordinate your interface’s behavior when an active SharePlay session supports spatial placement of content.

