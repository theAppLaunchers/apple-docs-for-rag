

- Group Activities
- SpatialTemplateSeatElement
-  seat(position:direction:role:) 

Type Method

# seat(position:direction:role:)

Creates a seat element with the specified position, direction, and role information.

visionOS 2.0+

``` source
static func seat(
    position: SpatialTemplateElementPosition,
    direction: SpatialTemplateElementDirection = .lookingAt(.app),
    role: (any SpatialTemplateRole)? = nil
) -> Self
```

Available when `Self` is `SpatialTemplateSeatElement`.

## Parameters 

`position`  

The position of this seat in the shared coordinate space. Place seats relative to your app’s content, which is at the origin of the coordinate space.

`direction`  

The initial direction for the participant to face. Specify a value to point the person in the direction of another participant or a specific location in the coordinate space. If you don’t specify this parameter, the participant faces the app’s content.

`role`  

The custom role you assign to the seat. Roles are optional but a way to make participant-specific decisions during an activity. For example, you might define roles for two opposing teams in a game and use those roles to place the participants relative to the game content.

## Return Value

An initialized seat element for you to add to a custom spatial template.

