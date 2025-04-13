

- WorkoutKit
- PacerWorkout
-  init(activity:location:distance:time:) 

Initializer

# init(activity:location:distance:time:)

Creates a new pacer workout for the specified distance and time.

iOS 17.0+iPadOS 17.0+Mac Catalyst 18.0+macOS 15.0+watchOS 10.0+

``` source
init(
    activity: HKWorkoutActivityType,
    location: HKWorkoutSessionLocationType = .unknown,
    distance: Measurement,
    time: Measurement
)
```

## Parameters 

`activity`  

The workout activity type.

`location`  

The workout location.

`distance`  

The distance goal for the workout.

`time`  

The time goal for the workout.

## See Also

### Creating a new pacer workout

static func supportsActivity(HKWorkoutActivityType) -> Bool

Returns a Boolean value that indicates whether the system supports pacer workouts for the given workout activity type.

