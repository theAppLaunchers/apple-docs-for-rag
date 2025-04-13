

- SwiftUI
- DismissBehavior
-  destructive 

Type Property

# destructive

The destructive dismiss behavior.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+visionOS 1.0+

``` source
static let destructive: DismissBehavior
```

## Discussion

Use this behavior when you want to dismiss a window regardless of any conditions that would normally prevent the dismissal. Dismissing windows in this matter may result in loss of state.

On macOS, this behavior will cause windows to dismiss even when they are currently showing a modal presentation, such as a sheet or alert. Additionally, a document window will not show the save dialog when there are unsaved changes and the window is dismissed with this behavior.

On iOS, this behavior behaves the same as `interactive`.

## See Also

### Getting behaviors

static let interactive: DismissBehavior

The interactive dismiss behavior.

