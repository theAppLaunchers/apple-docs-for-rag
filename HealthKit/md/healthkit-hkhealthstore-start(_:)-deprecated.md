

- HealthKit
- HKHealthStore
-  start(\_:) Deprecated

Instance Method

# start(\_:)

Starts a workout session for the current app.

watchOS 2.0–5.0Deprecated

``` source
func start(_ workoutSession: HKWorkoutSession)
```

Deprecated

Use HKWorkoutSession's start method

## Parameters 

`workoutSession`  

The workout session to start. You cannot restart a workout session that has stopped. If you pass in a session that is running or has stopped, the system returns an invalidArgumentException exception.

## Discussion

Workout sessions allow apps to run in the foreground. The current Foreground App appears when the user wakes the watch. Additionally, Apple Watch sets its sensors based on the workout activity and location types for more accurate measurements and better performance.

Apple Watch can only run one workout session at a time. If a second workout is started while your workout is running, your HKWorkoutSessionDelegate object receives an HKErrorAnotherWorkoutSession error, and your session ends.

This method returns immediately, however the work is performed asynchronously on an anonymous serial background queue. If successful, the session’s state transitions to HKWorkoutSessionState.running, and the system calls the session delegate’s workoutSession(_:didChangeTo:from:date:) method.

## See Also

### Deprecated symbols

func add([HKSample], to: HKWorkout, completion: (Bool, (any Error)?) -> Void)

Associates the provided samples with the specified workout.

Deprecated

func end(HKWorkoutSession)

Ends a workout session for the current app.

Deprecated

