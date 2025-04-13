

- WorkoutKit
- CustomWorkout
-  hash(into:) 

Instance Method

# hash(into:)

Hashes the essential components of the custom workout by feeding them into the given hash function.

iOS 17.0+iPadOS 17.0+watchOS 10.0+

``` source
func hash(into hasher: inout Hasher)
```

## See Also

### Comparing workouts

var hashValue: Int

The hashed value of the custom workout.

static func != (Self, Self) -> Bool

Returns a Boolean value that indicates whether two custom workouts aren’t equal.

static func == (CustomWorkout, CustomWorkout) -> Bool

Returns a Boolean value that indicates whether two custom workouts are equal.

