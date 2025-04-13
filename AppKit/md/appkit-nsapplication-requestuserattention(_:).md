

- AppKit
- NSApplication
-  requestUserAttention(\_:) 

Instance Method

# requestUserAttention(\_:)

Starts a user attention request.

macOS

``` source
@MainActor
func requestUserAttention(_ requestType: NSApplication.RequestUserAttentionType) -> Int
```

## Parameters 

`requestType`  

The severity of the request. For a list of possible values, see NSApplication.RequestUserAttentionType.

## Return Value

The identifier for the request. You can use this value to cancel the request later using the cancelUserAttentionRequest(_:) method.

## Discussion

Activating the app cancels the user attention request. A spoken notification will occur if spoken notifications are enabled. Sending requestUserAttention(_:) to an app that is already active has no effect.

If the inactive app presents a modal panel, this method will be invoked with `NSCriticalRequest` automatically. The modal panel is not brought to the front for an inactive app.

## See Also

### Managing User Attention Requests

enum RequestUserAttentionType

These constants specify the level of severity of a user attention request and are used by cancelUserAttentionRequest(_:) and requestUserAttention(_:).

func cancelUserAttentionRequest(Int)

Cancels a previous user attention request.

func reply(toOpenOrPrint: NSApplication.DelegateReply)

Handles errors that might occur when the user attempts to open or print files.

enum DelegateReply

Constants that indicate whether a copy or print operation was successful, was canceled, or failed.

