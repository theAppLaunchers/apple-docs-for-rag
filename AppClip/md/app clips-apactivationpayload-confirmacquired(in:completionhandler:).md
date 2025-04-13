

- App Clips
- APActivationPayload
-  confirmAcquired(in:completionHandler:) 

Instance Method

# confirmAcquired(in:completionHandler:)

Checks whether an App Clip invocation happened at an expected physical location.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

``` source
func confirmAcquired(
    in region: CLRegion,
    completionHandler: @escaping (Bool, (any Error)?) -> Void
)
```

``` source
func confirmAcquired(in region: CLRegion) async throws -> Bool
```

## Parameters 

`region`  

The expected physical location at the time of the App Clip invocation.

`completionHandler`  

A closure called when the platform confirms the expected physical location at the time of the App Clip invocation.

The closure takes the following parameters:

inRegion  
A Boolean value that indicates whether the App Clip invocation happened at the expected physical location.

error  
The error object that describes why the platform couldn’t confirm the user’s physical location.

This parameter is `nil` if the platform was able to determine the user’s physical location at the time of the App Clip invocation.

## Mentioned in 

Confirming a person’s physical location

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

Confirm the user’s location at the time of the App Clip invocation if the App Clip is associated with a physical location. The request to confirm the location fails with disallowed if the source of the invocation isn’t an NFC tag or visual code.

For the platform to accept the request to confirm the user’s location, you need to make modifications to the `Info.plist` file of the App Clip. For more information, see Enabling notifications in App Clips.

Note

Functionality to confirm the user’s location is only available to App Clips. For the full app, request permission to access the user’s location and make use of the Core Location framework. For more information, see Getting the current location of a device.

