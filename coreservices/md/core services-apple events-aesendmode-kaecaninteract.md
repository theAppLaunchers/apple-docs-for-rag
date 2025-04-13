

- Core Services
- Apple Events
- AESendMode
-  kAECanInteract 

Global Variable

# kAECanInteract

Mac Catalyst 13.0+macOS 10.0+

``` source
var kAECanInteract: Int { get }
```

## Discussion

The user interaction preference—the server application can interact with the user in response to the Apple event. By convention, you set the bit specified by this constant if the user needs to supply information to the server. If you set the bit and the server allows interaction, the `AEInteractWithUser(_:_:_:)` function either brings the server application to the foreground or posts a notification request. When you send an Apple event to a local application, the default is to set this bit.

