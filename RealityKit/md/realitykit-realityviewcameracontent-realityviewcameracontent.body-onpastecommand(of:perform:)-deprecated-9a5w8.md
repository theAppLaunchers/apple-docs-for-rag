

- RealityKit
- RealityViewCameraContent
- RealityViewCameraContent.Body
-  onPasteCommand(of:perform:) Deprecated

Instance Method

# onPasteCommand(of:perform:)

Adds an action to perform in response to the system’s Paste command.

RealityKitSwiftUImacOS 10.15–15.4Deprecated

``` source
nonisolated
func onPasteCommand(
    of supportedTypes: [String],
    perform payloadAction: @escaping ([NSItemProvider]) -> Void
) -> some View
```

Deprecated

Provide \`UTType\`s as the \`supportedContentTypes\` instead.

## Parameters 

`supportedTypes`  

The uniform type identifiers that describe the types of content this view can accept through a paste action. If the Clipboard doesn’t contain any of the supported types, the Paste command doesn’t trigger.

`payloadAction`  

The action to perform when the Paste command triggers. The action closure’s parameter contains items from the Clipboard with the types you specify in the `supportedTypes` parameter.

## Return Value

A view that triggers `action` when a system Paste command occurs.

## Discussion

Pass an array of uniform type identifiers to the `supportedTypes` parameter. Place the higher priority types closer to the beginning of the array. The Clipboard items that the `action` closure receives have the most preferred type out of all the types the source supports.

For example, if your app can handle plain text and rich text, but you prefer rich text, place the rich text type first in the array. If rich text is available when the paste action occurs, the `action` closure passes that rich text along.

