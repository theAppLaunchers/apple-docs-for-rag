

- WorkoutKit
- WorkoutStep
-  init(goal:alert:) 

Initializer

# init(goal:alert:)

Creates a new workout step with the provided goal and alerts.

iOS 17.0+iPadOS 17.0+Mac Catalyst 18.0+macOS 15.0+watchOS 10.0+

**Mac Catalyst, macOS, watchOS**

``` source
init(
    goal: WorkoutGoal = .open,
    alert: (any WorkoutAlert)? = nil
)
```

**iOS, iPadOS**

``` source
init(
    goal: WorkoutGoal = .open,
    alert: (WorkoutAlert)? = nil
)
```

## Parameters 

`goal`  

A goal that determines when the step ends.

`alert`  

Optional alerts used during the step.

