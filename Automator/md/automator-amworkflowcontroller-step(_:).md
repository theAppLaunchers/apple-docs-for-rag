

- Automator
- AMWorkflowController
-  step(\_:) 

Instance Method

# step(\_:)

In a paused workflow, runs the next action in the workflow and then pauses again.

Mac Catalyst 14.0+macOS 10.4+

``` source
@IBAction @MainActor
func step(_ sender: Any)
```

## Parameters 

`sender`  

Object that initiated the step action.

## Discussion

Stepping allows a workflow to be executed one action at a time. This is useful for ensuring that the workflow is doing what it’s supposed to do, as the results of each individual action can be inspected before moving on to the next.

## See Also

### Controlling the Workflow

func pause(Any)

Pauses a workflow that’s running.

func reset(Any)

Stops a workflow, clears any action results, and resets the workflow back to an un-run state.

func run(Any)

Runs the associated workflow, after first clearing any results stored by its actions during any previous run.

func stop(Any)

Stops the associated workflow.

