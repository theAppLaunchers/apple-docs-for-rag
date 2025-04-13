

- FamilyControls
- FamilyActivityPicker
-  textSelection(\_:) 

Instance Method

# textSelection(\_:)

Controls whether people can select text within this view.

FamilyControlsSwiftUIiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
nonisolated
func textSelection(_ selectability: S) -> some View where S : TextSelectability
```

## Discussion

People sometimes need to copy useful information from `Text` views — including error messages, serial numbers, or IP addresses — so they can then paste the text into another context. Enable text selection to let people select text in a platform-appropriate way.

You can apply this method to an individual text view, or to a container to make each contained text view selectable. In the following example, the person using the app can select text that shows the date of an event or the name or email of any of the event participants:

```
var body: some View {
    VStack {
        Text("Event Invite")
            .font(.title)
        Text(invite.date.formatted(date: .long, time: .shortened))
            .textSelection(.enabled)

        List(invite.recipients) { recipient in
            VStack (alignment: .leading) {
                Text(recipient.name)
                Text(recipient.email)
                    .foregroundStyle(.secondary)
            }
        }
        .textSelection(.enabled)
    }
    .navigationTitle("New Invitation")
}
```

On macOS, people use the mouse or trackpad to select a range of text, which they can quickly copy by choosing Edit \> Copy, or with the standard keyboard shortcut.

On iOS, the person using the app touches and holds on a selectable `Text` view, which brings up a system menu with menu items appropriate for the current context. These menu items operate on the entire contents of the `Text` view; the person can’t select a range of text like they can on macOS.

Note

`Button` views don’t support text selection.

