

- SwiftUI
- TextSelectability
-  enabled 

Type Property

# enabled

A selectability value that enables text selection by a person using your app.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+

``` source
static var enabled: EnabledTextSelectability { get }
```

Available when `Self` is `EnabledTextSelectability`.

## Discussion

Enabling text selection allows people to perform actions on the text content, such as copying and sharing. Enable text selection in views where those operations are useful, such as copying unique IDs or error messages. This allows people to paste the data into emails or documents.

The following example enables text selection on the second of two Text views in a VStack.

```
VStack {
    Text("Event Invite")
        .font(.title)
    Text(invite.date.formatted(date: .long, time: .shortened))
        .textSelection(.enabled)
}
```

## See Also

### Getting selectability options

static var disabled: DisabledTextSelectability

A selectability value that disables text selection by the person using your app.

