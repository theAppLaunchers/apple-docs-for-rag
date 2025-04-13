

- WorkoutKit
- WorkoutPlan
- WorkoutPlan.Workout
-  hash(into:) 

Instance Method

# hash(into:)

Hashes the essential components of the workout by feeding them into the given hash function.

iOS 17.0+iPadOS 17.0+watchOS 10.0+

``` source
func hash(into hasher: inout Hasher)
```

## See Also

### Comparing workout plans

var hashValue: Int

The hashed value of the workout.

static func != (Self, Self) -> Bool

Returns a Boolean value that indicates whether two workouts aren’t equal.

static func == (WorkoutPlan.Workout, WorkoutPlan.Workout) -> Bool

Returns a Boolean value that indicates whether two workouts are equal.

