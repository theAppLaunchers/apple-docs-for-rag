

- HomeKit
- HMTrigger
-  removeActionSet(\_:completionHandler:) 

Instance Method

# removeActionSet(\_:completionHandler:)

Removes an action set from the trigger.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+visionOS 1.0+

``` source
func removeActionSet(
    _ actionSet: HMActionSet,
    completionHandler completion: @escaping ((any Error)?) -> Void
)
```

``` source
func removeActionSet(_ actionSet: HMActionSet) async throws
```

## Parameters 

`actionSet`  

The action set to remove.

`completion`  

The block executed after the request is processed.

error  
`nil` on success; otherwise, error object indicating the reason for failure.

## See Also

### Managing Action Sets

var actionSets: [HMActionSet]

Array of all action sets that will be executed by the trigger.

func addActionSet(HMActionSet, completionHandler: ((any Error)?) -> Void)

Adds an action set to the trigger.

