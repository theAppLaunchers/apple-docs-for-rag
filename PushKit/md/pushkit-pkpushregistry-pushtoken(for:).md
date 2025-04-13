

- PushKit
- PKPushRegistry
-  pushToken(for:) 

Instance Method

# pushToken(for:)

Retrieves the locally cached push token for the specified push type.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.15+visionOS 1.0+watchOS 6.0+

``` source
func pushToken(for type: PKPushType) -> Data?
```

## Parameters 

`type`  

A push type requested by this push registry object. For a list of possible types, see PKPushType.

## Return Value

The push token used to send pushes to the device or `nil` if no token is available for the specified type.

## Discussion

If registration for a specific push type is successful, the push registry delivers the corresponding push token to its delegate and adds a copy of the token to its local cache. Use this method to retrieve the token at a later time.

## See Also

### Managing the Push Registry

var desiredPushTypes: Set&lt;PKPushType>?

Registers the push types for this push registry object.

