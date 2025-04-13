

- Assignables
- AssignableDocumentView
-  refreshable(action:) 

Instance Method

# refreshable(action:)

Marks this view as refreshable.

AssignablesSwiftUIiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOSwatchOS 8.0+

``` source
nonisolated
func refreshable(action: @escaping () async -> Void) -> some View
```

## Parameters 

`action`  

An asynchronous handler that SwiftUI executes when the user requests a refresh. Use this handler to initiate an update of model data displayed in the modified view. Use `await` in front of any asynchronous calls inside the handler.

## Return Value

A view with a new refresh action in its environment.

## Discussion

Apply this modifier to a view to set the `EnvironmentValues/refresh` value in the view’s environment to a `RefreshAction` instance that uses the specified `action` as its handler. Views that detect the presence of the instance can change their appearance to provide a way for the user to execute the handler.

For example, when you apply this modifier on iOS and iPadOS to a `List`, the list enables a standard pull-to-refresh gesture that refreshes the list contents. When the user drags the top of the scrollable area downward, the view reveals a progress indicator and executes the specified handler. The indicator remains visible for the duration of the refresh, which runs asynchronously:

```
List(mailbox.conversations) { conversation in
    ConversationCell(conversation)
}
.refreshable {
    await mailbox.fetch()
}
```

You can add refresh capability to your own views as well. For information on how to do that, see `RefreshAction`.

