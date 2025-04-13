

- PushKit
- PKPushRegistryDelegate
-  pushRegistry(\_:didUpdate:for:) 

Instance Method

# pushRegistry(\_:didUpdate:for:)

Tells the delegate that the system updated the credentials for the specified type of push notification.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.15+visionOS 1.0+watchOS 6.0+

``` source
func pushRegistry(
    _ registry: PKPushRegistry,
    didUpdate pushCredentials: PKPushCredentials,
    for type: PKPushType
)
```

**Required**

## Parameters 

`registry`  

The PKPushRegistry instance responsible for the delegate callback.

`type`  

One of the requested notification types. This type is present in the desiredPushTypes property of the push registry.

## Mentioned in 

Supporting PushKit Notifications in Your App

## Discussion

The system calls this method when it receives new credentials (including a push token) for the specified push type.

## See Also

### Responding to Registration Events

func pushRegistry(PKPushRegistry, didInvalidatePushTokenFor: PKPushType)

Tells the delegate that the system invalidated the push token for the specified type.

