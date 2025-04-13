

- ManagedAppDistribution
- ManagedContentView
-  onChange(of:initial:\_:) 

Instance Method

# onChange(of:initial:\_:)

Adds a modifier for this view that fires an action when a specific value changes.

ManagedAppDistributionSwiftUIiOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 17.0+watchOS 10.0+

``` source
nonisolated
func onChange(
    of value: V,
    initial: Bool = false,
    _ action: @escaping () -> Void
) -> some View where V : Equatable
```

## Parameters 

`value`  

The value to check against when determining whether to run the closure.

`initial`  

Whether the action should be run when this view initially appears.

`action`  

A closure to run when the value changes.

## Return Value

A view that fires an action when the specified value changes.

## Discussion

You can use `onChange` to trigger a side effect as the result of a value changing, such as an `Environment` key or a `Binding`.

The system may call the action closure on the main actor, so avoid long-running tasks in the closure. If you need to perform such tasks, detach an asynchronous background task.

When the value changes, the new version of the closure will be called, so any captured values will have their values from the time that the observed value has its new value. In the following code example, `PlayerView` calls into its model when `playState` changes model.

```
struct PlayerView: View {
    var episode: Episode
    @State private var playState: PlayState = .paused

    var body: some View {
        VStack {
            Text(episode.title)
            Text(episode.showTitle)
            PlayButton(playState: $playState)
        }
        .onChange(of: playState) {
            model.playStateDidChange(state: playState)
        }
    }
}
```

