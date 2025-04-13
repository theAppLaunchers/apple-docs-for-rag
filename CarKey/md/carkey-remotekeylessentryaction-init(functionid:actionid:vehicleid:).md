

- CarKey
- RemoteKeylessEntryAction
-  init(functionID:actionID:vehicleID:) 

Initializer

# init(functionID:actionID:vehicleID:)

Creates a new action object with the specified action-specific details and vehicle ID.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.3+watchOS 9.0+

``` source
init(
    functionID: FunctionIdentifier,
    actionID: ActionIdentifier,
    vehicleID: String
)
```

## Parameters 

`functionID`  

The vehicle-specific code that identifies the feature to activate. For example, the vehicle might have a specific code to access the door locks.

`actionID`  

The vehicle-specific code that defines what action to take on the vehicle feature. For example, a vehicle might have separate actions to lock and unlock the vehicle’s doors.

`vehicleID`  

The target vehicle for the action. Choose the vehicle from one of the session’s vehicle reports. Specify the string in the identifier property of the corresponding report.

## Return Value

An action object with the specified information.

## Discussion

This method creates an immutable action object that you can pass to your session’s perform(_:) method.

