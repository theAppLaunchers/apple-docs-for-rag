

- Group Activities
- GroupSession
-  systemCoordinator 

Instance Property

# systemCoordinator

The system coordinator associated with an active session.

visionOS 1.0+

``` source
final var systemCoordinator: SystemCoordinator? { get async }
```

Available when `ActivityType` conforms to `GroupActivity`.

## Discussion

After you join an activity, access this property to determine if a system coordinator object is available. The system coordinator informs you when the device supports spatial Personas, and when the current participant’s spatial Persona is available to use in the current activity. When a spatial Persona is available, update the information you share for the activity and how you present that content. For more information, see SystemCoordinator.

