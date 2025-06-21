Framework

# WorkoutKit

Create, preview, and sync workout compositions to the Workout app.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+watchOS 10.0+

## [Overview](/documentation/WorkoutKit#overview)

The WorkoutKit framework provides models and utilities for creating and previewing workouts in your iOS and watchOS apps, and for syncing scheduled workouts to the Workout app on Apple Watch. The framework supports the following types of workouts:

[`CustomWorkout`](/documentation/workoutkit/customworkout)

A structured interval workout with a series of steps containing custom goals and alerts

[`SingleGoalWorkout`](/documentation/workoutkit/singlegoalworkout)

A workout with a single goal, such as distance, energy, or time

[`PacerWorkout`](/documentation/workoutkit/pacerworkout)

A workout with distance and time goals

[`SwimBikeRunWorkout`](/documentation/workoutkit/swimbikerunworkout)

A workout that allows triathletes to seamlessly transition between swim, bike, and run activities

You define a workout by initializing one of these workout types. Then you use the workout to create a [`WorkoutPlan`](/documentation/workoutkit/workoutplan), which provides methods for previewing, syncing, or exporting the plan. To open the plan in Workout on Apple Watch, call [`openInWorkoutApp()`](/documentation/workoutkit/workoutplan/openinworkoutapp\(\)). To export the plan, call the `dataRepresentation(as:)` method.

You can also use WorkoutKit to create and maintain a workout schedule and, with the user’s permission, sync scheduled compositions to Apple Watch. These compositions appear in a dedicated space in the Workout app and include your app’s icon and name.

Before you can schedule a workout, you must ask for permission. Get the shared [`WorkoutScheduler`](/documentation/workoutkit/workoutscheduler) instance, and call its [`requestAuthorization()`](/documentation/workoutkit/workoutscheduler/requestauthorization\(\)) method. Then call the [`schedule(_:at:)`](/documentation/workoutkit/workoutscheduler/schedule\(_:at:\)) method to schedule workouts.

To access health data for the workout, see the [HealthKit](/documentation/HealthKit) framework.

## [Topics](/documentation/WorkoutKit#topics)

### [Essentials](/documentation/WorkoutKit#Essentials)

[

Customizing workouts with WorkoutKit](/documentation/workoutkit/customizing-workouts-with-workoutkit)

Create, preview, and sync workouts for use in the Workout app on Apple Watch.

### [Common workouts](/documentation/WorkoutKit#Common-workouts)

```swift
```swift
```swift
```swift
struct SingleGoalWorkout
```
```

A workout with a single goal.
```
```swift
```swift
```swift
struct PacerWorkout
```
```

A workout in which a person covers a specific distance in a given time.
```
```swift
```swift
```swift
struct SwimBikeRunWorkout
```
```

A workout for multisport activities that include running, biking, and swimming.
```
```

### [Custom interval workouts](/documentation/WorkoutKit#Custom-interval-workouts)

```swift
```swift
```swift
```swift
struct CustomWorkout
```
```

A workout that includes a repeating series of work and recovery steps.
```
```swift
```swift
```swift
struct WorkoutStep
```
```

A step in a workout.
```
```swift
```swift
```swift
struct IntervalBlock
```
```

Blocks of work and recovery steps that repeat in a custom workout.
```
```swift
```swift
```swift
struct IntervalStep
```
```

An interval that represents a work or recovery step in a workout.
```
```swift
```swift
```swift
enum WorkoutGoal
```
```

A value that specifies the goal for a workout.
```
```swift
```swift
```swift
protocol WorkoutAlert
```
```

An alert that notifies the user of significant events during a workout.
```
```

### [Workout plans and schedules](/documentation/WorkoutKit#Workout-plans-and-schedules)

```swift
```swift
```swift
```swift
struct WorkoutPlan
```
```

A wrapper around a workout object that your app can use to open the object in Workout or schedule it for later.
```
```swift
```swift
```swift
struct ScheduledWorkoutPlan
```
```

A wrapper around a workout plan that your app can use to schedule the workout plan.
```
```swift
```swift
```swift
class WorkoutScheduler
```
```

An object for scheduling and managing workouts.
```
```

### [Errors](/documentation/WorkoutKit#Errors)

```swift
```swift
```swift
```swift
enum StateError
```
```

An error that occurs while previewing a workout composition.
```
```