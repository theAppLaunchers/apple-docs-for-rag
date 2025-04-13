

- SwiftUI
- View
-  onScrollTargetVisibilityChange(idType:threshold:\_:) 

Instance Method

# onScrollTargetVisibilityChange(idType:threshold:\_:)

Adds an action to be called with information about what views would be considered visible.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
nonisolated
func onScrollTargetVisibilityChange(
    idType: ID.Type,
    threshold: Double = 0.5,
    _ action: @escaping ([ID]) -> Void
) -> some View where ID : Hashable
```

## Parameters 

`idType`  

The type of Identity provided by the subviews.

`threshold`  

The amount required to be visible within the viewport of the the scrollview before the `action` is fired. By default when the view has crossed more than 50% on-screen, the action will be called.

`action`  

The action which will be called when the views within the scroll view cross the provided threshold. The callback will include which views are considered visible.

## Discussion

Use this modifier along with the modifier `View/scrollTargetLayout()` to be informed when the views in the targetted scroll view have crossed the provided threshold to be considered on/off screen.

```
ScrollView {
    LazyVStack {
        ForEach(models) { model in
            CardView(model: model)
        }
    }
    .scrollTargetLayout()
}
.onScrollTargetVisibilityChange(for: Model.ID.self, threshold: 0.2) { onScreenCards in
    // Disable video playback for cards that are offscreen...
}
```

## See Also

### Responding to scroll view changes

func onScrollGeometryChange&lt;T>(for: T.Type, of: (ScrollGeometry) -> T, action: (T, T) -> Void) -> some View

Adds an action to be performed when a value, created from a scroll geometry, changes.

func onScrollVisibilityChange(threshold: Double, (Bool) -> Void) -> some View

Adds an action to be called when the view crosses the threshold to be considered on/off screen.

func onScrollPhaseChange(_:)

Adds an action to perform when the scroll phase of the first scroll view in the hierarchy changes.

struct ScrollGeometry

A type that defines the geometry of a scroll view.

enum ScrollPhase

A type that describes the state of a scroll gesture of a scrollable view like a scroll view.

struct ScrollPhaseChangeContext

A type that provides you with more content when the phase of a scroll view changes.

